---
title: "WoW on portable harddrive"
date: 2011-01-09
forum: Wine
---

### Post by Blacktalon on 2011-01-09
Hello everyone,

So here's what's up, my desktop got trashed.  I just got a 1TB portable hard drive; I am wondering if there is away to install and run World of Warcraft from a portable harddrive.  The other desktop I am wanting to do this with, meets all the requirements to run WoW, but I really want to keeping reinstalling it every time something happens to my desktops.  I just need to know if there is away to run it from a portable harddrive, and how.

Thank you,
~BT

---

### Post by gyussz on 2011-01-09
Hey,

WoW should work fine If you copy your whole World of Warcraft directory to the portable drive. By the way WoW doesn't need to be installed every time you reinstall your system, unless you have only one partition ofc. You may have to run it with Launcher.exe so it can recreate the common folders, registry entries etc.

Anyway I'm not sure about portable drive performance, fps may be lower if you run wow on it, but it depends on the drive.

---

### Post by cwwilson721 on 2011-01-09
It would run fine IF you use the following to launch the program:

```
env WINEPREFIX="<LOCATION OF EXTERNAL WINE DRIVE MOUNT POINT>" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl
```

And use ```
env WINEPREFIX="<LOCATION OF EXTERNAL WINE DRIVE MOUNT POINT>" winecfg
```to setup the 'wine drive'.

I would use the winecfg command to setup the 'drive' first, then install WoW to that (I prefer a copy from Windows myself. So much less hassles). If you NEED to install to the external HDD from wine, do a Google search for the proper procedures.

---

