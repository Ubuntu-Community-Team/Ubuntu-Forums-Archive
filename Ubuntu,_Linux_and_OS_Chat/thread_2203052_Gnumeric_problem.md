---
title: "Gnumeric problem"
date: 2014-02-01
forum: Ubuntu, Linux and OS Chat
---

### Post by artemus_86 on 2014-02-01
Hello all,

I would like to ask for some advice regarding spreadsheet program Gnumeric. 
I am using Linux Mint 15 and the installed version of Gnumeric is 1.12.1.

I would like to multiply two matrices with in a spreadsheet, but for some reason Gnumeric just calculates the first cell of an array. I have read from the documentation page ([https://projects.gnome.org/gnumeric/doc/sect-data-formulas.shtml#sect-data-formulas-array](https://projects.gnome.org/gnumeric/doc/sect-data-formulas.shtml#sect-data-formulas-array)) that the correct procedure for this would be to first select the 4x4 array containing the result, then entering the command ```
=mmult(M2:P5,M7:P10)
``` and then finishing by pressing Ctrl+Shift+Enter. However, only the first cell is calculated.

I must be doing something wrong... I only know that this way works in MS Excel although the two arrays inside mmult() -command are separated by a semicolon instead of comma.
[ATTACH=CONFIG]249990[/ATTACH]

---

### Post by tgalati4 on 2014-02-01
Paste the mmult in each cell, then it should calculate the dot product for each cell in the resulting matrix.

---

### Post by artemus_86 on 2014-02-01
I tried to copy/paste the mmult() to each cell, but the result is not correct as the selection moves with the cell. If I fix the selection with "$", each of the cells get a value of 53.

I tried to follow the documentation ([https://help.gnome.org/users/gnumeric/stable/quick-data.html.en#quick-data-input-formula](https://help.gnome.org/users/gnumeric/stable/quick-data.html.en#quick-data-input-formula)):
> [INDENT]Certain functions return not just a single value but an array of         values. To enter such a function, first select a range of cells         to receive the result, then enter the formula to generate the         array, and then press the key combination     Ctrl+Shift+Enter     rather than just the Enter key. For more     details see [Section 5.2.4.5 &#8213; Array Formulas]("https://help.gnome.org/users/gnumeric/stable/sect-data-types.html.en#sect-data-formulas-array").
[/INDENT]


There's something that I don't understand about the array operations of Gnumeric.

[ATTACH=CONFIG]250010[/ATTACH]

---

### Post by steeldriver on 2014-02-01
Try selecting the whole 4x4 array of cells where you want the output to go, then clicking back in the formula entry area and **then **hitting Ctrl-Shift-Enter

---

### Post by artemus_86 on 2014-02-01
> **steeldriver said:**
> Try selecting the whole 4x4 array of cells where you want the output to go, then clicking back in the formula entry area and **then **hitting Ctrl-Shift-Enter

Yes, it works now! My technique was faulty.
Many thanks!
[ATTACH=CONFIG]250011[/ATTACH]

---

### Post by steeldriver on 2014-02-01
Glad to help! entering array functions confuses me every (rare) time I try to use them - fwiw it's the same procedure in Excel I think

---

