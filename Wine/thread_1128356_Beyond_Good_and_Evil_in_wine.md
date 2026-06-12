---
title: "Beyond Good and Evil in wine"
date: 2009-04-17
forum: Wine
---

### Post by wildman4god on 2009-04-17
does any one know if I can get the mentioned game to work in wine, I am willing to do what ever cli tricks necessary to make it work, I did check the wine db and it only lists the steam version, I am buying the PC version on a CD-ROM. Anybody want to help?

---

### Post by u235sentinel on 2009-04-17
> **wildman4god said:**
> does any one know if I can get the mentioned game to work in wine, I am willing to do what ever cli tricks necessary to make it work, I did check the wine db and it only lists the steam version, I am buying the PC version on a CD-ROM. Anybody want to help?

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2604](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2604)

Looks like they are at silver support for it at best.  I'm willing to bet you would have sufficient problems that it would drive you crazy to run under WINE at this time.  But you could always try and get lucky :D

Good Luck!

---

### Post by wildman4god on 2009-04-17
> **u235sentinel said:**
> [http://appdb.winehq.org/objectManager.php?sClass=application&iId=2604](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2604)

Looks like they are at silver support for it at best.  I'm willing to bet you would have sufficient problems that it would drive you crazy to run under WINE at this time.  But you could always try and get lucky :D

Good Luck!

well I have heard of some users adding some dll files and tweaking wine a bit to get some games to work, could I do this?

---

### Post by NightMKoder on 2009-04-17
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7929&iTestingId=24474](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7929&iTestingId=24474)

Seems relatively easy - install as usual, patch, add the registry key, and all (except sound?) is well.

If something fails, make sure you have a clean wine prefix.

---

### Post by cogadh on 2009-04-17
> **wildman4god said:**
> well I have heard of some users adding some dll files and tweaking wine a bit to get some games to work, could I do this?
The first step to doing that is doing what others have already done, as described in the AppDB pages already linked. Adding/overriding DLLs and "tweaking" Wine is only necessary to correct specific problems with the application you are trying to run. For example, if you run the game and Wine complains about some missing functionality in a DLL, then you should try replacing that DLL with a Windows native one to see if that helps. There really are no general overrides or tweaks that anyone can say for certain will help with the game, but if you try running the game and get some problems, we may be able to offer specific advice based on the actual problems you encounter.

---

