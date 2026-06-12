---
title: "DOS, Windows 95, and Windows 2000 on three partitions: How?"
date: 2009-02-06
forum: Windows
---

### Post by dbsoundman on 2009-02-06
I'm at a loss here. I'm trying to figure out how people out there have installed several Windows OSes (old ones at that) to separate partitions on a hard disk. What I have right now is an 80GB drive divided as follows:
2GB FAT16 (DOS)
20GB FAT32 (WIN95)
20GB FAT32 (WIN2K)
And the rest goes to Ubuntu and swap, in an extended partition.

Right now I have GRUB setup, installed in the Ubuntu partition as far as I can tell, and I have custom configured it to load each OS. I setup hide/unhide options for the Windows/DOS partitions to hide them from each other, and leave only their partition visible.

My PROBLEM is I can't figure out how I can get Windows 95 in particular on the second partition. I already have DOS on the first partition (which was of course easy as pie), but I have the Windows 95 OEM package, which comes with a boot floppy with fdisk and stuff like that on it, and a non-bootable CDROM to install the OS. I'm assuming the easiest thing to do would be to install DOS on the second partition with CD-ROM support, and then install Windows 95 from there. But how do I install DOS on the second partition? I was thinking there HAS to be a way to boot into a partition or something like that, but I have not a clue how to do that. For that matter, could I just mount the second partition through Ubuntu and copy the DOS install files over there? Would that boot up all right? *I may go try that now actually...*

Anyway, any helpful advice would be appreciated, I'm running out of ideas here.

Thanks,
Dan

---

### Post by Dr. C on 2009-02-06
One idea is to dispense with DOS and use the the version of DOS in Windows 95 instead. It is highly compatible with DOS 6.22. In fact one can even install Windows 3.1 on the Win 95 DOS. The following link explains how to boot DOS from Windows 95 / 98. 
[http://www.computerhope.com/issues/ch000132.htm]("http://www.computerhope.com/issues/ch000132.htm")
To get the Windows 95 environment one simply types```
Win
``` at the DOS prompt just like in the Windows 3.1 / 3.11 days.

Also not all the versions of Windows 95 support FAT 32, and I would keep the DOS / Windows 95 partition under 2 GB

---

### Post by bm40 on 2009-02-07
[http://www.justlinux.com/forum/showthread.php?t=147959](http://www.justlinux.com/forum/showthread.php?t=147959)

Just a thought

---

