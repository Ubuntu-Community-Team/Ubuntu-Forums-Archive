---
title: "[SOLVED] gThumb. photo import problem"
date: 2008-12-27
forum: Ubuntu Studio
---

### Post by OldGrey on 2008-12-27
Hi

I am running Ubuntu 8.10. This is a problem whihc is new to me though I have downloaded many photos in the past from my Camera (Canon 400D SLR). When I connect the camera via the usb lead. I am given the option of opening the files with F Spot or gThumb. I chose gThumb (F Spot does not agree with my PC), the program opens and I click on import and I get the following error message

[INDENT][I]An error occurred in the io-library ('Could not lock the device'): Camera is already in use.
[/I][/INDENT]

Annoyingly I can import with F Spot.

How can I stop this happening? It has not happened before.

---

### Post by callan79 on 2008-12-28
> **OldGrey said:**
> An error occurred in the io-library ('Could not lock the device'): Camera is already in use. Annoyingly I can import with F Spot.
How can I stop this happening? It has not happened before.


Hi OldGrey,

I know what you mean - this problem is annoying. And I can't stand F-Spot.

The solution seems to be that you have to unmount the camera first. I have a Canon 350D and a Canon A620. When I connect either one, I get a "Canon..." icon on the desktop, the same as you would get for a USB drive.

If you right click and UNMOUNT, you can then go ahead and use gThumb no problem.

There's also some talk about this [here](http://ubuntuforums.org/showthread.php?t=967104)

Good luck.

Callan

---

### Post by OldGrey on 2008-12-28
Thanks Callan, worked a treat.

---

### Post by raydar on 2008-12-29
Thanks, Callan--worked for me too, with a Kodak EasyShare C653.

---

### Post by hocmin on 2009-01-25
Worked perfectly for me on my Nikon D40.  Does anyone know if this has been marked as a bug, is being worked on, etc?

---

