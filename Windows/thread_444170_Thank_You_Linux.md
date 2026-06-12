---
title: "Thank You Linux"
date: 2007-05-15
forum: Windows
---

### Post by theringoffire67 on 2007-05-15
Man, I had a problem, I went screwing around with my windows boot and logon screens.  I messed something up and my computer was coming up with "ntfs.sys" error message and wouldn't let me go into safe mode or anything, no boot anything.

Thank God I had Ubuntu duel booted on my laptop because the Windows Xp cds weren't doing jack.  So, I was able to copy over my backed up files that I saved even though they were NTSC and everything booted nicely.  Thank you Linux :)

---

### Post by LaRoza on 2007-05-15
RESOLUTION
To resolve this problem, replace the missing or corrupted Ntfs.sys file:
1.	Use the Windows XP startup disks or the Windows XP CD to restart your computer.
2.	When the "Welcome to Setup" screen appears, press R to select the To repair a Windows XP installation using Recovery Console, press R option.
3.	Type the number of the Windows installation that you want to access from the Recovery Console, and then press ENTER.
4.	Type the administrator password when you are prompted, and then press ENTER. If no administrator password exists, just press ENTER.
5.	At the command prompt, type the following commands (press ENTER after each command):
cd \windows\system32\drivers

ren ntfs.sys ntfs.old
Note This step renames the corrupted Ntfs.sys file to Ntfs.old. If the Ntfs.sys file is not found, the file is missing.
6.	At the command prompt, type the following command, and then press ENTER:
copy cd:\i386\ntfs.sys drive:\windows\system32\drivers
Where cd is the drive letter for the CD-ROM drive that contains the Windows XP CD, and drive is the drive where you installed Windows XP.
7.	Remove the Windows XP CD from your CD-ROM drive, type quit at a command prompt, and then press ENTER to quit the Recovery Console.
8.	Restart the computer.


Snippet from:
[http://support.microsoft.com/kb/822800](http://support.microsoft.com/kb/822800)

---

### Post by marx2k on 2007-05-16
> **theringoffire67 said:**
> Thank God I had Ubuntu duel booted on my laptop because the Windows Xp cds weren't doing jack.  So, I was able to copy over my backed up files that I saved even though they were NTSC and everything booted nicely.  Thank you Linux :)

Thank goodness the files weren't saved in PAL :lolflag:

---

