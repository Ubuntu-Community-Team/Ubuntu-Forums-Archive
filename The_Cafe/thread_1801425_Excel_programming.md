---
title: "Excel programming"
date: 2011-07-10
forum: The Cafe
---

### Post by Sceiron on 2011-07-10
Hoi,
im playing around in Excel, does anyone have any tips for how to check if a cell in MS Excel can do the following:

I wanna check if a cell contains "ABC" in a cell with xxx1980
Lets say cell A contains ABC1980 then what I need excel to do:

IF Cell A contains ABC1980
print Yes in Cell B
IF Cell A contains DEF1980
print maybe in Cell B

I have tried with MID function, and CODE function without good results.
any Excel geeks :) ?
Had problems finding compare-functions that looks for charaters..
Thanx

---

### Post by Bachstelze on 2011-07-10
Look at the IF() function.

---

### Post by Sceiron on 2011-07-10
Thats what I have been doing, but how to get it to focus on just the letters in the cell..


edit:
SOLVED :)
IF(ISNUMBER(SEARCH(ABC;B));Yes;Maybe)

---

