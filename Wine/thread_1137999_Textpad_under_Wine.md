---
title: "Textpad under Wine"
date: 2009-04-26
forum: Wine
---

### Post by vertigo420 on 2009-04-26
hi there,

just installed textpad under wine, runs just fine. but when i double click a file on my desktop which is associated with it, lets say "/home/user/Desktop/file.ext", textpad runs and asks if i want to create the file "z:\home\user\ome\user\Desktop\file.ext", as if it cant find the file. running textpad first and then opening the file from the menu works fine.

dragging a file into textpad also works ok.

any ideas how to integrate with the shell more smoothly?

---

### Post by vertigo420 on 2009-04-26
just tried opening from /opt, textpad fails again, interpreting the filename as "/pt/file.ext".

looks as if its an issue with wine or textpad using the opening slash as an escape character? notepad.exe does something similar.

---

### Post by asdfoo on 2009-04-26
which Wine version? 1.1.20 is the latest

---

### Post by vertigo420 on 2009-04-26
i have the latest stable version, 1.0.1, i also tried updating to 1.1.20 unstable and apt-get failed with a missing dependancy that it couldnt find any repo, including the winehq repo.

---

### Post by sgosnell on 2009-04-26
Any particular reason you want to go to the trouble of running textpad in wine, when there are many native Linux text editors that are more capable and user friendly?

---

### Post by vertigo420 on 2009-04-26
its what ive used for programming for years and years. if you know of a substitute in linux that has all the features textpad has, im all ears.

---

### Post by sgosnell on 2009-04-27
I don't know all the features it has, but have you tried gedit?  It has more than most Windows editors I've tried, and I tried a lot over the years.  Notetab Pro was the last one I used, and I don't miss it at all.  There are probably more text editors available for Linux than Windows, because Linux geeks tend to be programmers, and they're all free.

---

### Post by eilios on 2009-04-27
I usually use Kate for programming, although IDE's are better, Kate is a good plain text editor.

---

