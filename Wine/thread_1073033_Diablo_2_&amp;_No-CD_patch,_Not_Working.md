---
title: "Diablo 2 &amp; No-CD patch, Not Working"
date: 2009-02-17
forum: Wine
---

### Post by Sugi on 2009-02-17
I just installed Diablo 2 over the weeken at a lan party and everything went well except for one thing.  I can not get Diablo 2 running without a cd with the official no cd patch.  I am running on 1.12b patch from a full installation of Diablo 2 direct from the cd.  (thank you wine eject -a)  If anyone knows about the official no cd patch, you know you have to copy the D2xMusic.mpq from the cd and drop it into your Diablo 2 directory.  Which I did, but when I try to load it up.  I get a little window sayings please insert the cd.  But the odd thing is, everyone else did the same thing from the same cd (of course they did it on window's though) and it worked for them.  So, I tried to change the caps of the file and see if that had any affect on it.  (d2xmusic.mpq, D2xMusic.MPQ, etc. etc.)  But still the same error message.

Does anyone have a clue on how to get this running?

My current workaround is to mount a image of the LOD cd and run the game through wine.  A side note, I couldn't get LOD cd to work on my distro (ubuntu couldn't see the anything ont he disc).  So I made an image of the disc and install the game through that.


Installed:
Diablo 2 
Diablo 2 LOD
Wine 1.1.7
Ubuntu Hardy Heron 8.04

Sugi

---

### Post by Sugi on 2009-02-19
bump

---

### Post by Meow27 on 2009-02-19
[http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=49](http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=49)


[http://appdb.winehq.org/objectManager.php?sClass=version&iId=315](http://appdb.winehq.org/objectManager.php?sClass=version&iId=315)


check this link and the bottom link for different versions of Wine

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by Sugi on 2009-02-21
Meow27, I don't get how this helps me.  Did I overlook something here.  My problem is, I can't get Diablo 2 to run with the d2xmusic file i copied to my hard drive, but it should run without the cd.

Sugi

---

### Post by Sugi on 2009-02-22
bump

---

### Post by NightMKoder on 2009-02-22
> 
Copy Protection Final Word

Patch 1.12 from Blizzard disables the CD check.

If you ever get "Please insert disc", this is NOT a problem with detecting the CD. The protection system is probably still built into the game even though the CD check itself is disabled. Make sure you use version 1.12 or later. If you get this problem after having this version installed, you are likely suffering from a buggy video driver as this is the only known (and proven possible) cause at this point.

DO NOT USE NOCD PATCHES - They are pointless, and won't fix the real problem.


from the first link. What's your video card/driver?

---

### Post by Sugi on 2009-02-25
I have laptop GPU GeForce 7700 GO and the drivers..... I'll get those details for you when I get home.  I used the Hardware Drivers for my graphi card, but that's all I can tell you off hand.

Sugi

---

### Post by karth on 2009-02-26
As far as I remember you have to copy d2xvideo.mpq into the Diablo II install directory as well, along with d2xmusic.mpq

All the files on my system have lower case filenames.

See attached capture:

---

