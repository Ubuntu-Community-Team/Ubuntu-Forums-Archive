---
title: "Kayboard-oriented/Emacs-like spreadsheet editor?"
date: 2011-09-16
forum: The Cafe
---

### Post by Zorgoth on 2011-09-16
I was just using LibreOffice Calc to do a massive grade entry job, and comparing using Calc to edit spreadsheets to how fast I can use emacs to edit code, it really, really fails in many, many respects.  

This is not so much of an attack on Calc (whose purpose is to service "real-world" people, not keyboard junkies), as a hope that someone out there has developed something to fill the niche of keyboard addicted coders who sometimes have to edit spreadsheets.

Has anyone developed a spreadsheet editor that can handle Microsoft formats and does these things?  Or has some blessed soul created an xls-compatible spreadsheet editor for emacs?  Or is it possible to modify LibreOffice to be more like this?  Emacs isn't actually quite ideal - something more graphics capable would be better - I guess my dream would be something like Calc, only with a minibuffer and fewer windows.  Or am I stuck in the land of GUIs unless I make my own :P

Here's some examples of things that would be handled better by an emacs-like spreadsheet editor (from my perspective).

a) Having a separate Find and Replace window in the first place is really inconvenient when if makes you defocus the spreadsheet and thus steals your arrow keys - the window also i) covers part of the spreadsheet and ii) has to be closed (while in emacs search is cancelled by many commands, including arrow keys, not just ESC).  Emacs-style search handles this much better.

b) Emacs search is interactive, Calc search is not

c) Searching backwards and doing regular expressions requires selecting More Options... in the find and replace window, whereas with emacs these are all a single keypress - particularly, Backwards should be a lot easier to access, as I frequently overshoot my target.

d) As far as I can tell, to return to the start of my search in Calc I have to scroll all the way back, while in Emacs I could just press C-x C-x

e) Navigator (F5) is a quite inefficient tool to move to a specific column by keyboard - it doesn't even autoselect the column, so you have to remember to type delete before the name of your column; moreover, the window doesn't close when you press enter, but does defocus, so you are forced to click in order to close it after using it.  You could easily imagine that an emacs-like spreadsheet editor would have an interactive column search that would take you to whatever column you wanted by letter in 2 or 3 quick keypresses, while preserving your current row.

---

### Post by matthew.ball on 2011-09-16
Have you checked out [org-mode]("http://orgmode.org/") for emacs?

In particular, the [built-in table editor]("http://www.gnu.org/software/emacs/manual/html_node/org/Built_002din-table-editor.html"). It doesn't *look* fantastic, but it gets the job done.

---

### Post by Zorgoth on 2011-09-23
That *does* look like something interesting that I should check out sometime, but unfortunately I am entering data into .xls files that are provided to me, so unless there is some kind of very good import/export function, which is something Google does not seem encouraging about, it won't work for what I'm doing :(

---

