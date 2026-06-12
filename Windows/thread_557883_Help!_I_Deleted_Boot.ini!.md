---
title: "Help! I Deleted Boot.ini!"
date: 2007-09-23
forum: Windows
---

### Post by Ian505 on 2007-09-23
Okay, I am really lost. Last night I was cleaning up my C:\ directory because it had a lot of crap that Norton Ghost put there. I made sure that system files were hidden before deleting a file called boot.ini that was not even a hidden file. (nice job Norton...) Now, when I booted up my computer, windows wouldn't boot due to a hal.dll error. I researched a bit and found that it is sometimes caused by a corrupt or missing boot.ini and knew right away that that was the problem. I found my XP CD and made my way to the recovery console and typed **BOOTCFG /REBUILD** but when it scanned for windows on my drives (I have 2) it couldn't find it and gave me an error saying that the drive may be corrupt and that you should run chkdsk. Did that- no problems. **WHAT DO I DO!**

I do have a copy of SuperGRUB disk from a previous boot problem... if that would help.

Thanks in advance.
-Ian

---

### Post by por100pre1 on 2007-09-23
Check [this]("http://mirror.href.com/thestarman/asm/mbr/bootini.htm"). Hope it helps. :)

---

### Post by Ian505 on 2007-09-23
> **por100pre1 said:**
> Check [this]("http://mirror.href.com/thestarman/asm/mbr/bootini.htm"). Hope it helps. :)

This helps describe what the BOOT.INI file is.. but it doesn't help me in my situation.

Also.... my chk dsk just finished and it said that Alpha (my windows drive) had one or more errors on it.... but that was all.

HELP PLEASE!

---

### Post by Ian505 on 2007-09-23
I was wondering if a Windows Repair Installation would delete all of my files or reformat my drive. If it does, I cant do it because I have about 50GB of important info, docs and images on the windows drive. 

-Ian

EDIT- Nevermind. this isnt an option for me.... only as a last resort.

---

### Post by aidanr on 2007-09-23
If you're dual booting you can write a new boot.ini to your windows drive from ubuntu using the info por100pre1 linked to.

You'll need to install [ntfs-3g]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G") for that.

---

### Post by Ian505 on 2007-09-23
> **aidanr said:**
> If you're dual booting you can write a new boot.ini to your windows drive from ubuntu using the info por100pre1 linked to.

You'll need to install [ntfs-3g]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G") for that.

OOOHHHHH! Okay I will try that.

---

### Post by por100pre1 on 2007-09-23
Sorry to differ, but the link I gave you points to [this]("http://support.microsoft.com/default.aspx?scid=kb;en-us;289022") page with a sample Boot.ini and details.

---

### Post by Ian505 on 2007-09-23
Okay... I cant get ntfs-3g to work.
 I have been working on this for hours... and I am tired of working on it I am going to take a break for now.

EDIT- Found the problem- installin ntfs-3g

---

### Post by kulturloseramerikaner on 2007-09-23
I've had to do at least 2 repair installs on my 'doze partition; it does not cause you to lose anything except for some settings.  It does, however, take over an hour to do, so if you do get ntfs-3g and have a valid BOOT.INI you can simply copy, that'll be much faster.  Just remember to put it back in the same directory you deleted it from, or else you'll have the same issue; if I remember correctly, it's one of those files that 'doze always puts/looks for in the same directory.

---

