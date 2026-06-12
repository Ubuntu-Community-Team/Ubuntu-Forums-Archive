---
title: "[SOLVED] Cannot start Windows XP in Virtual Box"
date: 2007-12-18
forum: Virtualisation
---

### Post by TidusBlade on 2007-12-18
I installed XP on Virtualbox and it worked perfectly for days, but now, whenever I try to start it up, it says Failed to start the Virtual machine Windows XP.  And then spits out this error:
```

Unknown error creating VM (VERR_FILE_NOT_FOUND).
VBox status code: -102 (VERR_FILE_NOT_FOUND).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```
Any help appreciated :D

---

### Post by kay65535 on 2007-12-18
It looks like VirtualBox can't find the hard-disk image where WinXP is installed. Did you move any folders inside your home folder? ".virtualbox" folder maybe?

---

### Post by TidusBlade on 2007-12-18
Nope, I didnt, I even tried making another XP machine, and reinstalled VB...
ooooh... Sephiroth :p

---

### Post by Caharin on 2008-01-03
I am getting the exact same error.  It happened right after I created a second xp machine, the first one stopped working.  I cant even select the old vdi as a slave to the new machine (by the way my new machine works fine.)

---

### Post by TidusBlade on 2008-01-03
Ill try creating a new one the next time I get the error, for now, I uninstalled it and reinstalled it a week later, and working perfectly at the moment.

---

### Post by satisha on 2008-02-19
Try disabling the dvdrom if you have that  set to mount.

---

### Post by PmDematagoda on 2008-02-19
This thread has been moved to the Virtualisation section.

---

