[![NPM version](https://img.shields.io/npm/v/@thyrith/momentkh.svg)](https://www.npmjs.com/package/@thyrith/momentkh)
[![GitHub issues](https://img.shields.io/github/issues/ThyrithSor/momentkh.svg)](https://github.com/ThyrithSor/momentkh/issues)
[![GitHub forks](https://img.shields.io/github/forks/ThyrithSor/momentkh.svg)]()
[![GitHub stars](https://img.shields.io/github/stars/ThyrithSor/momentkh.svg)]()
[![GitHub license](https://img.shields.io/github/license/ThyrithSor/momentkh.svg)]()

# momentkh
momentkh is an add-on feature to moment js library

## Install ๐
```
$ npm install moment --save
$ npm install @thyrith/momentkh --save
```

## How to use ๐ซ
This library is built depends on [moment.js](https://momentjs.com) popular library.
We added some functionality to make it easier to work with Khmer date format.

### Nodejs
```javascript
const moment = require('moment');
// Add our features to your preferred moment.js version
require('@thyrith/momentkh')(moment);

// From now on, your moment js is transformed

let today = moment();

console.log(today);
// Display date today as moment js object
// For example: moment("2018-12-15T14:49:38.586")

let khmerDate = today.toLunarDate();

console.log(khmerDate);
// Display khmer date
// For example: แแแแแแแแ แจแแพแ แแแแทแแแทแ แแแแถแแ แแแแนแแแแแแ แแปแแแแแแแถแ แขแฅแฆแข
```

### HTML
First, you need to clone this package to the root of your project or your `/public` folder.

\*\*\* *For `momentjs` library, you can import it any method or any version you want.*

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.29.1/moment.min.js"></script>
<script src="momentkh/constant.js"></script>
<script src="momentkh/locale/km.js"></script>
<script src="momentkh/getSoriyatraLerngSak.js"></script>
<script src="momentkh/momentkh.js"></script>
<script>
	var moment = momentkh(moment)
	var today = moment()
	console.log('Today: ', today.toKhDate())
	console.log('New year at: ', moment.getKhNewYearMoment(2021))
</script>
```

## Added Functionality ๐ก

#### Attributes of moment instance
| Name  | Parameter | Description | Example |
|---------|-------|---------|----------------|
|toLunarDate| *empty* or String |display format as Khmer lunar date | ``moment().toLunarDate();`` |
|khDay| *empty* |display khmer day index | ``moment().khDay();`` <br/> 0 -> แกแแพแ<br/> 1 -> แขแแพแ<br/> 2 -> แฃแแพแ<br/> ... <br/>15 -> แกแแแ <br/>16 -> แขแแแ <br/>17 -> แฃแแแ<br/> ...|
|khMonth| *empty* |display khmer month index | ``moment.khMonth();`` <br/>0 -> แแทแแแทแ <br/> 1 -> แแปแแแ <br/> 2 -> แแถแ <br/> 3 -> แแแแแปแ <br/> 4 -> แแแแแ <br/> 5 -> แแทแแถแ <br/> 6 -> แแแแแ <br/> 7 -> แขแถแแถแ <br/> 8 -> แแแแถแแแ <br/> 9 -> แแแแแแ <br/> 10 -> แขแแแแปแ <br/> 11 -> แแแแแทแ <br/> 12 -> แแแแถแแถแ <br/> 13 -> แแปแแทแแถแแถแ<br/>|
|khYear| *empty* |display Buddhist Era year | ``moment().khYear();`` |

##### *Alias*
| Name  | Original |
|---------|----------------|
|toKhDate, tokhdate|toLunarDate|


#### Attributes of moment

| Name  | Parameter | Description | Example |
|---------|-----|-----------|----------------|
|getKhNewYearMoment| Integer | Return moment.js object. Giving the moment of Khmer New Year. (แแแแแแแแถแแปแ) | `moment.getKhNewYearMoment(2019);`|
|~~readLunarDate~~*(currently working on this)*| String or Object |Return moment.js object. Just same as calling: ``moment('13/04/2018', 'dd/mm/yyyy');`` for Gregorian date </br> |``moment.readLunarDate('แกแฅแแพแ แแทแแถแ แ.แ. แขแฅแฅแฅ');`` |

##### *Alias*
| Name  | Original |
|---------|----------------|
|khDate, khdate|readLunarDate|

## Format
By default, it will return the format as shown in example above.
However, you can also customize your format.

```javascript
// Use moment.js as usual. Documentaion: momentjs.com
let myBirthday = moment('4/3/1992', 'd/m/yyy');

myBirthday.toLunarDate('dN แแแแW แแm แ.แ. b');
// แฆแแพแ แแแแแแแแ?แแแแแทแ แแแแทแแแทแ แ.แ. แขแฅแฆแข'
```

| Format  | Description | Example |
|---------|----------------|----------------|
| W | แแแแแแแแแแแถแ?แ| แขแแแแถแ |
| w | แแแแแแแแแแแถแ?แแแถแแ | แข |
| d | แแแแแแธ แแถแแแแธแแแ แก แแแ แกแฅ      | แก      |
| D | แแแแแแธ แแถแแแแธแแแ แ?แก แแแ แกแฅ | แ?แก |
| n | แแพแ แฌ แแแ | แ |
| N | แแพแ แฌ แแแ | แแพแ |
| o | แแแแแแแแแแแแแธแขแแแธแแแแแแธ | แงก (แแถแแแแแแถ แกแแพแ)|
| m | แแแแแแแแแท | แแทแแแทแ |
| M | แแแแปแแทแแแแท | แแแแถ |
| a | แแแแถแแแแแ | แแแถ |
| e | แแแ | แฏแแแแ |
| b | แแแแถแแแปแแแแแแแถแ | แขแฅแฅแฆ |
| c | แแแแถแแแแแทแแแแแแแถแ| แขแ?แกแฉ |
| j | แแแแถแแแปแแแแแแแถแ | แกแคแฆแฃ |

# Bug Report ๐๐๐ฆ๐ท๐ธ๐ฆ๐ฆ๐๐๐ฃ
I know there will be a lot of error.

# Testing
There is no test running on this package. If you are available for this work, it would be very awesome.

# Contribute ๐ก
Welcome pull request 

# References
* [แแแแถแแแแแแแแแถแแปแ](http://www.dahlina.com/education/khmer_new_year_time.html?fbclid=IwAR0Eq6US-F0LfplMjKzmiRn7rvPgi31i74Wpv4mNhU034mzdyj-3hYrCA8w)
* [แแแแแทแแทแแแแแแแแท](http://www.cam-cc.org)

# Support me
I'm really happy if this project is useful to you.

If you would like to buy me some breakfast, here is my ABA account number: **000 485 222**. Don't forget to remark `momentkh` so that I can count it as usefulness of my work.
