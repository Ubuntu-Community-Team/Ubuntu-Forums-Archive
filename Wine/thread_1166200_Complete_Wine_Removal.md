---
title: "Complete Wine Removal"
date: 2009-05-21
forum: Wine
---

### Post by ToyotaGuy23 on 2009-05-21
Hello,

I installed Wine, and attempted to install the Safari browser.  It worked, but I elected to check for updates, and later learned that I shouldn't have.  Safari installed, but will not run.  

What I have tried to do is remove wine completely, and start over.

sudo apt-get remove wine
autoremove
deleted wine files from /.local/share/applications/wine/Programs

how can i wipe wine and ALL of it's (registry) or installed programs and ALL traces of Wine so I can reinstall and try again?

---

### Post by Meow27 on 2009-05-21
all it should take is to delete the .wine directory in the home folder, no need to reinstall or remove wine, just kill that folder and install safari again, your system files will be copied from your system back into the .win folder so you should be able to start from scratch.

if that fails, you might have a problem with your system.

---

### Post by Devilman13 on 2009-05-21
I've had the same issue with it just leaving random crap behind or shortcuts or whatever.

If you type:
```
locate wine
```

in a terminal it will tell you all locations of anything Wine related after you uninstall.

Your safari probably is located in /home/yourloginname/.wine

---

### Post by cogadh on 2009-05-21
In the future, just follow Meow27's advice and just delete the .wine directory from your home directory. That will eliminate everything you have installed with Wine and restore Wine back to its default state.

---

