# Crossword Solver

![Demo](http://i.imgur.com/aFWu4GB.gif)

Solve crosswords that have been created with www.crossword-compiler.com

## Try it out

1. Copy the minified source code,
2. Open up a your crossword website ([Example](http://v.postimees.ee/ristsona/Veebiristsonad/Veebiristsona106-14012016/Veebiristsona106-14012016.html)
3. paste the code to the Chrome Dev tools Console and
4. check out the cool process

```javascript
function CrossWordSolver(){"use strict";let squares=$(".GridSquare.Let");let alphabet="abcdefghijklmnopqrstuvwxyz".toUpperCase().split("");var a=0;var intervalId;function solve(){intervalId=setInterval(bruteForce,400)}function bruteForce(){var letter=alphabet[a];for(var i=0;i<squares.length;i+=1){bruteForceSquare($(squares[i]))}clickCheckButton();checkIfSolved()}function bruteForceSquare(square){var x=getXSignFrom(square);if(!needsFilling(square,x)){return}removeSignFrom(x);giveARightStylingFor(square);writeLetterInto(square)}function getXSignFrom(square){if(square.find("div")){return $(square.find("div")[1])}}function needsFilling(square,x){return!square.find("p span").html()||x&&x.attr("style")=="opacity: 1;"}function removeSignFrom(x){x.attr("style","opacity: 0;")}function giveARightStylingFor(square){square.find("p span").attr("style","color: black; font-weight: bolder; font-size: 35.7px; line-height: 1;");square.find("p").attr("style","width: 100%; text-align: center; font-family: sans-serif; font-weight: normal; position: absolute; margin-top: 19.9px; font-size: 1px;")}function writeLetterInto(square){square.find("p span").html(alphabet[a])}function clickCheckButton(){$(".ButtonText")[0].click()}function checkIfSolved(){if(++a>=alphabet.length){clearInterval(intervalId)}}return{solve:solve}}new CrossWordSolver().solve();
```

## License

[MIT](//github.com/ukupat/crossword-solver/blob/master/LICENSE)
