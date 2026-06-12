---
title: "Starcraft CD isnt recognized"
date: 2010-05-17
forum: Wine
---

### Post by azizzle on 2010-05-17
I was able to install starcraft in wine, however now when i attempt to play it i get an error message saying "file needed not found, please make sure disc is in drive..." it's mounted. I can't figure out what to do. Any ideas?

---

### Post by jbrown96 on 2010-05-17
You probably need to add the drive in ```
winecfg
``` Go to Drives tab and add a drive. The drive doesn't matter, just change the path to ```
/dev/cdrom
``` and the type to CD-ROM. That should fix the problem.

---

### Post by azizzle on 2010-05-17
thanks, that worked

---

### Post by Dayofswords on 2010-05-17
> ---------------------
- patch 1.15.2
---------------------
  Feature Changes

- StarCraft and StarCraft: BroodWar no longer require the CD while playing the game.  To play without the CD, please follow the following instructions:

Windows Users:
- Make sure you have "Hide extensions for known types" unchecked. To do this please use the following steps:
    - Click Start -> Programs -> Accessories -> Windows Explorer
    - Click on Tools -> Folder options (Windows Vista users may have to press the Alt key to see the tools option at the top of the window)
    - Click on the View Tab In the list, look for the "Hide extensions for known file types" option, and make sure that it is unchecked.
    - Click OK to save the changes.
    - Now you will need to copy some files from the Game CDs

- If you own only StarCraft, copy "INSTALL.EXE" from the StarCraft CD to your StarCraft folder and rename it to "StarCraft.mpq".

- If you own StarCraft: Brood War, copy "INSTALL.EXE" from the StarCraft: Brood War CD to your StarCraft folder and rename it to "BroodWar.mpq".  If you wish to play the StarCraft original missions then please copy and rename the install file from the original StarCraft CD as well, as listed directly above.
if you translate this into how you would do this in the wine folder, you wont need the cd

---

### Post by TwiztidJ on 2010-08-27
Hi, y'all. I'm new to using wine. I am having this same problem. I tried what was suggested but it was unsuccessful. One thing interesting is that /media/SCdisk1. I tried using that default plus the adding of another drive and still no luck. I have seen many different approaches to the drive letter setup and I have tried just about all of them but they were all not use-able. If anyone could help me out, that would be great.
Thanks

---

