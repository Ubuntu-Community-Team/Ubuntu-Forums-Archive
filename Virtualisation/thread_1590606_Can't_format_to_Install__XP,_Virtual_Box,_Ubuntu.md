---
title: "Can't format to Install  XP, Virtual Box, Ubuntu"
date: 2010-10-08
forum: Virtualisation
---

### Post by FredVanH on 2010-10-08
Hi.  My Ubuntu 10.4 installation got screwed up by a faulty download of updates and now I can't get the gnome shell or any other command to work.  I want to format its drive, install Win XP, Virtual Box and guest Ubuntu.  I have 4 XP Upgrade install discs from the past;  but none of them will boot up.  On two of them, I get the XP Install procedure to go as far as the Setup Welcome Screen;  but then they freeze.  With the other 2, they're ignored and the Ubuntu login screen comes up.

This computer, an HP a6357c-b, was built in 2007 and came with Vista, which was taken off in favor of Ubuntu.  My XP disks are from @ 2003.

1)  Is it possible that without the deformed Ubuntu stuff on there, the XP Install disks might "take"?
2)  Anyone know how I may format my hard drive (500GB) without an XP Install disk?  - maybe even with a newly installed Ubuntu 10.4?
Thanks for any help,
Fred

---

### Post by Scunizi on 2010-10-08
If you still have the live cd boot to that and use the partition manager to delete the partitions on the drive.. then create one partition out of the entire drive and format it with either ntfs or fat32.. when done try the xp cd's again.. but you may still have issues because they are upgrade cd's.. good luck

---

### Post by scrooge_74 on 2010-10-09
Can you boot in safe mode in Ubuntu and use a recovery shell? MAybe your X is just the one giving you problems.

If you have a Live CD you can just either delete partions and start fresh or recover the PC.

---

### Post by DanPerecky on 2010-10-09
If I'm reading your post correctly, you are saying that your XP portions of the HD are non-operative...

Some things I learned... that may or may not be common knowledge. Bottom line- use NTFS for Windows, not FAT32. FAT32 will cause you grief with regards to virtualization.

> FAT32...  You cannot create/have a filesize larger than (2^32)-1 bytes  (this is one byte less than 4 GB) on a FAT32 partition ... MS  Quote.

> Also: You cannot format a volume larger than 32GB in size using FAT32To format partitions, I use the free pkg: gparted: Gnome Partition Editor. [http://www.gparted.org/](http://www.gparted.org/) It's a standalone pkg. You burn the cd, then boot your pc with it. I've had no problems making Linux and NTFS partitions. There was a slight problem experienced when trying to resize an NTFS partition. It was supposed to work, but for some reason gparted corrupted it instead- caution. Well, maybe it was just me/my pc (thank God for backups). Creating an NTFS partition (in the same space on my HD) was fine. Once the NTFS partition is created, and before any software is installed, run chkdsk / defrag from a Windows cd/dvd- to make sure.

---

### Post by Dragynn on 2010-10-09
> **danperecky said:**
> if i'm reading your post correctly, you are saying that your entire hd is non-operative, and that you want to re-install both ubuntu and xp?

Some things i learned... That may or may not be common knowledge. Bottom line- use ntfs for windows, not fat32. Fat32 will cause you grief with regards to virtualization.

 ... Ms  quote.

To format partitions, i use the free pkg: Gparted: Gnome partition editor. [http://www.gparted.org/](http://www.gparted.org/) it's a standalone pkg. You burn the cd, then boot your pc with it. I've had no problems making linux and ntfs partitions. There was a slight problem experienced when trying to resize an ntfs partition. It was supposed to work, but for some reason gparted corrupted it instead- caution. Well, maybe it was just me/my pc (thank god for backups). Creating an ntfs partition (in the same space on my hd) was fine. Once the ntfs partition created and before any software is installed, run chkdsk / defrag from a windows cd/dvd, to make sure.

If your entire pc needs reconfiguring, and all of your partitions are askew, then it could be your partition table. If this is the case, and you are comfortable with totally redoing your pc (there is no data left to back up)... You can start with the 'create a partition table' option.

+1

---

### Post by DanPerecky on 2010-10-09
Oh... another thing... If your Ubuntu install(s) are simmering nicely, and you want to install Windows in a different partition... You will not be able to boot Ubuntu after the Windows install. Windows usually thinks it's the king of the PC when installed... 

Unless you or someone else knows of any nifty tricks to make Ubuntu to be visible and bootable, a reinstall of Ubuntu may be necessary after the Windows install. Plan accordingly.

---

### Post by wilee-nilee on 2010-10-10
4 discs sounds like a OEM set if this is the case I doubt you will get anywhere in a virtual, if they have a built in key activation.

---

