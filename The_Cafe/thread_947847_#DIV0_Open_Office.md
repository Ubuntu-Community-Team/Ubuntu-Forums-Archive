---
title: "#DIV/0 Open Office"
date: 2008-10-14
forum: The Cafe
---

### Post by OZFive on 2008-10-14
So I am making a spread sheet in Open Office and am using my limited knowledge to get it looking good.  The formulas are all in place and work well.  But I am running into issues with blank cells when I am having one divided by the other, it turns my sheet into a total mess with the phrase "#DIV/0" all over it in places.  Looks like crap.  I looked on the net and found a trick for MS Office that involved using Conditional Formatting were FORMULA IS  =ISERROR(C7/D7).  The choosing to have that formatted into white where it could not be seen.  I did that but it seems to interfering with my other Conditional Formatting I have in place and if I put it as Rule#1, Rules#2 & 3 do not come into play.  If I put it as Rule#3 it will not work.  

Is there something I can do different?

---

### Post by OZFive on 2008-10-14
Okay I got that problem solved.  Now I have just one thing left before I can call it perfect....

I have a Sum of a column that I am trying to get.  But in the Column there is a #DIV/0 and the total will not display.  The result is the dreaded #DIV/0

---

### Post by jespdj on 2008-10-14
I ofcourse don't know what you're doing (because you didn't explain in any detail what formulas you are using in your spreadsheet), but "#DIV/0" sounds as if you are making the program divide by zero.

You can't divide by zero, you get a math error if you do that.

Check your formulas. Are you doing any divisions in your formulas? Are you dividing by a value that might be zero (note that the contents of an empty cell might also be interpreted as zero)?

It sounds like a problem with your formulas, not like any bug or error in the software.

---

### Post by OZFive on 2008-10-14
No I know it is not an program error it is a formula error for sure.  Here is the deal...

the cell AC20 with the results formula is...

=SUM(AC8:AC19)

BUT cells AC8 - AC19 that have this formula in it...

=AB19-AA19

and those cells are reporting the #DIV/0

So the first formula cannot complete due to the second...

---

