---
title: "rotate pdf"
date: 2010-09-11
forum: The Cafe
---

### Post by chris200x9 on 2010-09-11
Does anyone know a program to rotate a pdf? I have school reading but it looks the the professor scanned a book so the page is sideways. Now I could read them like that because I'm super talented, but it'd be a huge PITA.

edit: should look under view before starting a tread :P

---

### Post by Mr. Picklesworth on 2010-09-11
In Evince (the default PDF viewer), go to Edit&#8250;Rotate in the menu and you're done.
If you do this quite frequently, you can add that to the toolbar. Right click it and select &#8220;Toolbar&#8221; to edit it.

---

### Post by Cyril_J on 2011-05-28
You can also [rotate PDF permanently]("http://www.rotatepdf.net/") with an online service. You'll have to do the operation only once, since the rotation is permanent.

---

### Post by doobydave on 2011-07-18
Why, why, why, why, why, why is this function in the 'edit' menu and not the 'view' menu.

Answers on a postcard..

---

### Post by DependencyHell on 2011-07-29
Hi!

Although this thread is marked as solved...i must share with you what i discovered today...
```
pdftk input.pdf cat 1-4 5E 6-end output rotated.pdf
```
rotates 5th page for 90 degrees
```
pdftk input.pdf cat 1-2 3S 4-end output rotated2.pdf
```
rotates 3rd page for 180 degrees

and i think this is cool!:popcorn:

---

