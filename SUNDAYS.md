# Sunday dash date generator 

To create the `sundaysYYYY.txt` files ...

```javascript
// creates list of Sunday dash dates YYYY-MM-DD
// sunday.js

const limit = 365;
const firstday = Date.parse('2022-01-01');

let day = 0;
let str = '';

const sunday = [];

for(let i = 0; i < limit; i++) {

    day = firstday + i * 86400 * 1000;
    str = (new Date(day)).toUTCString();
    if(isSunday(str)) {
        sunday.push(dashdate(day));
    }
}

console.log(sunday.join('\n'));

// returns true if UTC string is Sunday; otherwise, false
function isSunday(utcstring) {
    utcstring = '' + utcstring;
    const r = /^(Sun)\s*/;
    return !!utcstring.match(r);
}

// returns date in YYYY-MM-DD format given epoch time
function dashdate(epoch) {

    const date = new Date(epoch);

    dash = [];
    dash.push(date.getUTCFullYear());
    dash.push(pad(date.getUTCMonth() + 1));
    dash.push(pad(date.getUTCDate()));

    return dash.join('-');
}

// returns string in 00 format
function pad(str) {
    str = '' + str;
    return (str.length < 2) ? '0' + str : str;
}
```
