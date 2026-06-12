---
title: "open with default application.. from terminal.."
date: 2009-12-09
forum: The Cafe
---

### Post by anaconda on 2009-12-09
Is there any command to open a file from terminal with default application.. (like double-clicking in gnome)

eg. to open: 
.pdf with evince, 
picture with eog  (who even knew that the "image viewer":s actual name is eog???)
movie with vlc
.doc with openoffice

etc...

Sometimes the names of the programs can be difficult to remember.

And wouldn't it be cool to just type eg.
```
open ubuntu.pdf
```
instead of trying to remember what was the name of the program that opens pdf:s 

Is it already possible?

If not, it would be a cool little program for someone to make. :D

---

### Post by alphaniner on 2009-12-09
It would be pretty easy to write a script do do this, but you'd have to create tests and conditionals for each filetype you wanted to support.

PS: 'eog' is short for 'eye of gnome'.

---

### Post by 23meg on 2009-12-09
Try ```
xdg-open path_to_file
```.

---

### Post by Daisuke_Aramaki on 2009-12-09
Try setting up aliases in your .bashrc or .zshrc for different filetypes. You can just choose the file in your terminal and the program you setup for opening that file in your config will be invoked.

---

### Post by anaconda on 2009-12-09
> **23meg said:**
> Try ```
xdg-open path_to_file
```.

OMG !!!

It already exists.   :D

Thank you. You are a real command line GURU.

----

And I thought I had a really good NEW idea. I think I will make an easier (shorter) alias to that though..

---

