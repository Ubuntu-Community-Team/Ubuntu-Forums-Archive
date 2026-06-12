---
title: "Dual-boot issues. hal.dll missing/corrupted according to Windows-but it's not(I think"
date: 2008-08-25
forum: Windows
---

### Post by fiddler616 on 2008-08-25
Hello,
A few days ago I tried to install PuppyLinux on my USB drive, which did NOT go well (it went on a HD instead), and I couldn't even get to GRUB because it's boot loader wouldn't let me. Using Ubuntu's live CD, I deleted most of Puppy's bootloader files, (which didn't really help), backed up as much of /home as I could, and reinstalled Ubuntu to try and cut my losses. Ubuntu works great (nothing like a fresh install to speed up the system), but when I try to get to Windows XP (through GRUB, of course) it says something along the lines (may not be precisely verbatim) of:
Error, could not find
<root>\Windows\system32\ hal.dll
hal.dll may be missing or corrupted, please re-install it

I managed to hit F8 to get to the little menu where you can pick whether you want to Start Windows Normally, do Safe Mode, Last Known Good, whatever.
I tried both SM and LKG, and both displayed the same error.
I do not have a recovery CD for Windows.
I've looked at quite a few other threads, and one said that Windows doesn't like there to be OSs on partitions in front of it, and it led to an error in boot.ini it also gave instructions on fixing boot.ini, which I followed (I think), and it did nothing.
I'm sorry if I sound kind of terse, but I am.
I'm contemplating using gparted from a Live CD to wipe Ubuntu's partitions clean, and try to just boot up Windows like a normal MS user, and once that works, installing Ubuntu again, but I realized the best idea was to ask for some community support.
Thanks in advance.

---

### Post by fiddledd on 2008-08-25
Have a read [here](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm), ignore the System Restore option.

---

### Post by fiddler616 on 2008-08-25
All the 'meat' of that link thinks you have a Recovery Disk, which I don't :(

---

### Post by fiddledd on 2008-08-25
Then have a read [here](http://www.computerhope.com/issues/ch000635.htm), and follow the link for the recovery disks.

---

### Post by fiddler616 on 2008-08-25
I don't have a floppy drive.
Would using DosBOX instead work?

---

### Post by fiddledd on 2008-08-25
> **fiddler616 said:**
> I don't have a floppy drive.
Would using DosBOX instead work?

I've not tried it, it might work.

---

### Post by fiddler616 on 2008-08-26
I distinctly remember seeing DOSBox in the repositories, and now it's not. Am I going crazy?

---

