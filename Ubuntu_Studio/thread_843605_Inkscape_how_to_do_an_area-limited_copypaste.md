---
title: "Inkscape: how to do an area-limited copy/paste?"
date: 2008-06-28
forum: Ubuntu Studio
---

### Post by DMurray on 2008-06-28
Hi, all.

For the Inkscape artists out there, I need an advice.
Suppose you have some objects in a page, some of them are partially in the page, just what you want.
You can easily export just the page area by going to File/Export to Bitmap and select PAGE, it will save the file without considering what is outside the page.
Is it possible to do a selection which works this way? That is, the selection just marks portions of the objects, precisely what is inside the page, trimming what is outside, so you can paste in another project and do some other stuff.
Don't know if I made myself clear.
Thanks a lot.

---

### Post by ad_267 on 2008-06-28
I don't think there is an easy way to do this. Someone else might know a way though.

---

### Post by sub2007 on 2008-06-28
Inkscape is the most powerful graphics editor I've ever used, I think there's a way of doing **anything** related to vector graphics (and they still keep adding new stuff!). 
 
You can accomplish that with a clip path:

1. Draw a rectangle the size of a page on top of all the objects you want (so just trace out the outline of the page with a rectangle, doesn't matter about what fill you use). 
2. Then press CTRL+A to select all the objects on the page.
3. Go to Object > Clip > Set. The rectangle will not exist anymore, and you will be left with just the portion of the objects. You can then copy and paste that into anotjer project.

---

### Post by DMurray on 2008-06-30
Hi, my friends.
I will try the suggested steps as soon as I have my hands on my computer, right now I`m out of town, but BRB i a few days.
Thanks a lot.

---

### Post by DMurray on 2008-07-05
Holy sh1t!!!
It's just what I needed!!!! Thanks a lot, Sub2007!!! =D

---

