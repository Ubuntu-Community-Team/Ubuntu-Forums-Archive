---
title: "ubuntu server 7.1 installation woes"
date: 2008-04-13
forum: Server Platforms
---

### Post by andy_k on 2008-04-13
hi and sorry if this has been covered before but I'm completely confused..

trying to follow [this HowtoForge tutoria](http://www.howtoforge.com/ubuntu-home-fileserver-p3) everything goes smoothly until I reach section 8 which relies on me running fdisk -l

Apparently, I'm supposed top get a list of all the hard drives on my computer which will start with a line like

Disk /dev/hda: 33.8. GB, 33820286976 bytes

however, I'm not getting that,

Disk /dev/sda: 33.8. GB, 33820286976 bytes

I get this, it looks like  my IDE drives are are being read as SATA drives which seems to put an end to that (and all other) tutorial.

the second hard drive, which is formatted as NTFS reports the following


Device Boot   Start      End             Blocks        Id      System

/dev/sbd1         1        30401      244196001    7   HPFS/NTFS
/dev/sdb2  *     1           1                           0    0   Empty
Partition 2 does not end on cylinder boundary


This drive has been a Windoze drive for several months now but it was reformatted just before this installation.

Can anyone offer (in plain English please) a simple solution to this or point me to an online resource that makes creating a server a simple easy to follow task.

I'm trying to use the first hard drive as the file system and the second drive as the "store" for all our home office docs, media, photos etc

Thanks

Andy

---

### Post by ikonia on 2008-04-14
ubuntu 7.10 uses the new version of libata which shows ALL disks (ide/Sata/Scsi) as Scsi disks eg:

/dev/hda becomes /dev/sda

use this info and replace the wrong parts of the guide.

I also suggest if possible not using guides from external sites, [https://help.ubuntu.com](https://help.ubuntu.com) has some excellent guides that are ubuntu specific and maintained.

---

