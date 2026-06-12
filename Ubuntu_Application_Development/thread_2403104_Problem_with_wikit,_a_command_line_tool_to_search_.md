---
title: "Problem with wikit, a command line tool to search wikipedia on linux"
date: 2018-10-07
forum: Ubuntu Application Development
---

### Post by veran2018 on 2018-10-07
Hello a couple of weeks ago I installed wikit, a program for displaying summaries of Wikipedia articles on the linux terminal.

The command that I used for the installation was:

sudo npm install wikit -g

The answer shown in the terminal was:

npm WARN deprecated CSSselect@0.4.1: the module is now available as 'css-select'
npm WARN deprecated CSSwhat@0.4.7: the module is now available as 'css-what'
/usr/local/bin/wikit -> /usr/local/lib/node_modules/wikit/index.js
+ wikit@3.0.0
updated 1 package in 11.638s

I assumed that the program had been installed, but when making a query the result was the following:

argo@argo-desktop:~$ wikit Linux

/usr/local/bin/wikit: línea 2: use strict: orden no encontrada
/usr/local/bin/wikit: línea 4: error sintáctico cerca del elemento inesperado `('
/usr/local/bin/wikit: línea 4: `const path = require('path'),'

I'm not sure if this is the section where I should have published my query. If it is not, I apologize.

I have installed on my PC kubuntu 18.04.

From now on, thank you very much to anyone who can help me.


wikit github page
[https://github.com/KorySchneider/wikit](https://github.com/KorySchneider/wikit)

and 
[https://www.npmjs.com/package/wikit](https://www.npmjs.com/package/wikit)

---

