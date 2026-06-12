---
title: "Convert sudoku puzzles into svg/pdf, script and Inkscape ext."
date: 2011-03-30
forum: The Cafe
---

### Post by BkkBonanza on 2011-03-30
For SUDOKU aficionados,

I've created a script to take one-line puzzles and render them as SVG and/or PDF files. It has 6 basic svg templates for 1,2,6 up pages.

You can use it with a generator such as qqwing like this:

qqwing --generator 6 --one-line |**sudo2svg sudo6ltr.svg out**

This creates a one page svg graphic of 6 puzzles. It also can do auto conversion to PDF if you have Inkscape installed.

While I was at it I made an extention for Inkscape that makes it dead easy to place an array of NxN sudoku puzzles on a page.

If you are into sudoku puzzles and want to print your own batches easily...
all this (with a more extensive README) is in my archive at [Google Code]("http://code.google.com/p/sudo2svg/").

BTW I know that Gnome Sudoku can print puzzle sheets too. But this allows me more control and to use any source of puzzles such as a database.

---

