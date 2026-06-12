---
title: "I got Adobe After Effects 6.5 working in WINE!!!"
date: 2009-05-13
forum: The Cafe
---

### Post by AndThenWhat on 2009-05-13
Correct me if I am mistaken, but I thought that this was not possible until now.

Here's a Screenshot:

[http://img16.imageshack.us/img16/5822/screenshotxrr.png](http://img16.imageshack.us/img16/5822/screenshotxrr.png)

---

### Post by kevin11951 on 2009-05-13
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=648](http://appdb.winehq.org/objectManager.php?sClass=application&iId=648)

It has mixed reviews ;)

---

### Post by AndThenWhat on 2009-05-13
Yeah if you click those other ones they both say that the program crashes at the beginning. I've added a new WineHQ entry btw. Mine is platinum because the program runs and does everything correctly (even rendering movies)!

---

### Post by kevin11951 on 2009-05-13
> **AndThenWhat said:**
> Yeah if you click those other ones they both say that the program crashes at the beginning. I've added a new WineHQ entry btw. Mine is platinum because the program runs and does everything correctly (even rendering movies)!

which version of wine and after effects are you using?

---

### Post by AndThenWhat on 2009-05-13
WINE version 1.1.21 and After Effects 6.5

---

### Post by fatality_uk on 2009-05-13
Care to share how?

---

### Post by AndThenWhat on 2009-05-13
I actually did not do anything out of the ordinary I am amazed that I haven't heard of anyone else doing it. Here's what I did:

1. Install WINE 1.1.21 from here [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
2. Install After Effects 6.5 (The installer may seem to have crashed but just wait)
3. Set wine OS to Windows XP
4. Make sure Ubuntu has the latest updates
5. Go into Synaptic and remove the packages 'libgl1-mesa-dri' and 'libosmesa6'

That's it.

My Specs:

- Intel Centrino Duo (Dual Core)
- 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
- 2 GB RAM
- Ubuntu 9.04 Jaunty (Kernel 2.6.30-020630rc4-generic)

---

### Post by Delever on 2009-05-13
That's very interesting and useful. Thanks for trying!

---

### Post by AndThenWhat on 2009-05-13
I am going to put up a video later. In the meantime can other people try it and see if they can reproduce my results?

Cheers,

AndThenWhat

---

### Post by AndThenWhat on 2009-05-14
Okay, here is the video and a rather strange development.  It seems the reason I was getting an error about not being able to load an OpenGL plugin earlier was because of some packages I had to remove.  I completely removed the packages 'libgl1-mesa-dri' and 'libosmesa6' and suddenly the program works.

Video:

[http://www.youtube.com/watch?v=rdmVvuOjlmw](http://www.youtube.com/watch?v=rdmVvuOjlmw)

---

