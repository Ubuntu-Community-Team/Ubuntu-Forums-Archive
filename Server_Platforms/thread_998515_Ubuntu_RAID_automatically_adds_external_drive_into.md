---
title: "Ubuntu RAID automatically adds external drive into the pool"
date: 2008-11-30
forum: Server Platforms
---

### Post by dinkoarun on 2008-11-30
I have an Ubuntu 8.04 server installed in production. I setup the server to use two 250GB SATA Drives for Mirrored (software) RAID 0. The devices are known as SCSI Device A and Device B.

Now I add an external USB device mount on /media/disk to backup some data nightly. This device is known as SCSI Device C.

Originally, my Raid disks, /dev/md0 & /dev/md1, consisted of SCSI Device A and Device B. Once I added the external Device C, after a few hours, Device C gets automatically added to the Raid Disk.

I don't want this. I want my external device to be mounted as separate device where the backup disk can be removed and restored in case of emergency.

Any help would be appreciated.

---

### Post by fjgaude on 2008-11-30
After you have booted and the array is up and mounted, what does this show:

```
sudo mdadm -D /dev/md0
```

and also with md1?

---

### Post by dinkoarun on 2008-11-30
This is the reply I got after I rebooted:

> /dev/md0:
        Version : 00.90.03
  Creation Time : Sat Nov  8 17:15:25 2008
     Raid Level : raid1
     Array Size : 234468544 (223.61 GiB 240.10 GB)
  Used Dev Size : 234468544 (223.61 GiB 240.10 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Dec  1 10:00:52 2008
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 71d81ca7:3ff3552f:e05a9eec:5a6d8245
         Events : 0.27

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       


and for md1 I got:

>  
       /dev/md1:
        Version : 00.90.03
  Creation Time : Sat Nov  8 17:15:42 2008
     Raid Level : raid1
     Array Size : 9727232 (9.28 GiB 9.96 GB)
  Used Dev Size : 9727232 (9.28 GiB 9.96 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Mon Dec  1 09:55:54 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 004faae8:909dde2c:a8bb5470:ba20ceec
         Events : 0.6

    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       1       8       34        1      active sync /dev/sdc2

I know that /dev/sdc is the external USB device. What really surprises me is that it has removed the first Sata Device A (a.k.a /dev/sda) from the Raid Device list and has replaced it with the external usb device /dev/sdc.

What is happening? I need my Raid disks to consist of /dev/sda and /dev/sdb. Device /dev/sdc should be a separate device mounted on /media/disk

---

### Post by fjgaude on 2008-12-01
I think what is happening here is the names of the drives are getting changed when you add the USB one.

The array look as they should from the --detail command, so...

You might show this:

```
sudo fdisk -l
```

before adding the USB and after. That will be the tell tale.

---

