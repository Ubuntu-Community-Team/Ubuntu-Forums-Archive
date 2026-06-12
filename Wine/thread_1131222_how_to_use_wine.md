---
title: "how to use wine?"
date: 2009-04-20
forum: Wine
---

### Post by JakeHinojosa on 2009-04-20
ive downloaded wine and i want to open an exe file. what do i have to do to open it?i right clicked and chose open with wine. but it did nothing. can anybody help?

EDIT: figured out how to use it correctly. no longer need answers.

---

### Post by Bakon Jarser on 2009-04-20
That method should work.  It could be that the application you are trying to run won't work with wine.  Please check appdb for your program and see if others have gotten it to work.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by u235sentinel on 2009-04-21
> **Bakon Jarser said:**
> That method should work.  It could be that the application you are trying to run won't work with wine.  Please check appdb for your program and see if others have gotten it to work.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Yeah.  It's gotten better over the years.  I'm currently using 1.1.18 with greater success these days.  I've noticed some "oddities" here and there but generally I'm happy with WINE.  

always check the appdb before purchasing a program.  IMO you might get lucky and something will just work but then again when upgrading you might be frustrated as well with regressions.  Never know :D

---

### Post by Bakon Jarser on 2009-04-21
Also it could be copy protection.  If you are trying to run an .exe from a cd image that program might check to see if the disk is in the cd drive and not launch if it isn't.  Try launching the .exe from a terminal.  Go to the path where the .exe is and type 

wine (your .exe)

---

### Post by u235sentinel on 2009-04-22
> **Bakon Jarser said:**
> Also it could be copy protection.  If you are trying to run an .exe from a cd image that program might check to see if the disk is in the cd drive and not launch if it isn't.  Try launching the .exe from a terminal.  Go to the path where the .exe is and type 

wine (your .exe)

Hmmm... good point.  I've had a lot of success also with creating an image of the disk and mounting it.  The games run a heck of a lot faster now that I don't have to worry about the slower CD/DVD device :D

---

