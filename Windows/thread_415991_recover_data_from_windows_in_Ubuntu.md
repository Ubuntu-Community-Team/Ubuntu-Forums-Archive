---
title: "recover data from windows in Ubuntu?"
date: 2007-04-20
forum: Windows
---

### Post by brennydoogles on 2007-04-20
I am running a dual boot with Windows XP and Ubuntu, and recently my Windows XP drive has become corrupted. Whenever I attempt to boot into windows it begins to load, and then suddenly reboots. I cannot start in safe mode, and because it is a factory installation, I do not have a boot disk (only a recovery partition which will format over all of my data if i use it), and There are some family photos that I would really like to recover before I  try to reformat and/or replace the drive. The computer does have a Floppy drive, and my Ubuntu is on a second hard drive. My question is, how would I recover the data in Ubuntu, or if that is not possible, how can I download a DOS boot image to put on a floppy to use DOS to recover data and/or repair the drive (I have at leasta  basic knowledge of DOS commands). Thank you so much for your help!!

---

### Post by Dr. C on 2007-04-20
Ubuntu can read Windows partitions both NTFS and FAT. I would start here 

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/partitions-booting.html]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/partitions-booting.html")

---

### Post by brennydoogles on 2007-04-20
> **FineE said:**
> Ubuntu can read Windows partitions both NTFS and FAT. I would start here 

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/partitions-booting.html]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/partitions-booting.html")

I attempted to mount the partition, but it is showing up as empty. When i view it in Gparted however, it shows up as having 19 GB in use, and when I use NTFSFIX it tells me that the drive is corrupted. What I need is a way to boot the windows HD into DOS, so that I can either recover the files manually, or run CHKDSK and repair the drive. Thanks for the help!!

---

### Post by aysiu on 2007-04-20
Try this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

