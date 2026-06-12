---
title: "RAID6 Data Corruption"
date: 2014-11-11
forum: Server Platforms
---

### Post by RGee89 on 2014-11-11
I was trying to open a file through Samba when I noticed that it was corrupted. The Array is in a "clean, degraded" state, how could this correspond with corrupted files if the array is still intact? Some files seem to be okay, others are complete corrupted. Images seem to be partial corrupted because I can still load part of the image. I'm not too sure what I can do at this point...

Is there any way to scan through all the files in the Array to figure out what is corrupted? (atleast I can salvage the files that are not corrupted)

Any suggestions?

OS: Ubuntu 14.04
I'm using mdadm, software raid.

here is what my ```
mdadm --detail /dev/md0
``` currently says:

```

        Version : 1.2
  Creation Time : Mon Oct 14 10:07:29 2013
     Raid Level : raid6
     Array Size : 7813527552 (7451.56 GiB 8001.05 GB)
  Used Dev Size : 1953381888 (1862.89 GiB 2000.26 GB)
   Raid Devices : 6
  Total Devices : 6
    Persistence : Superblock is persistent


    Update Time : Tue Nov 11 13:46:19 2014
          State : clean, degraded, recovering
 Active Devices : 5
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 1


         Layout : left-symmetric
     Chunk Size : 512K


 Rebuild Status : 0% complete


           Name : myFS:0  (local to host myFS)
           UUID : db778c7d:dc15c8e9:067ddfca:92ca2bbf
         Events : 13340


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       7       8      113        1      active sync   /dev/sdh1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       6       8       33        5      spare rebuilding   /dev/sdc1

```

---

### Post by lukeiamyourfather on 2014-11-11
Sounds like silent data corruption which can come from a number of things (memory, cables, firmware, controller, vibration, software bugs, etc.). Do a RAID volume integrity check and do a file system check. This will find and fix what it can but it's possible that some of the data is lost for good due to the corruption. Unless you're using a file system with checksums there won't be a way to tell what is or isn't actually corrupted until the application level. In the past I've run into silent data corruption with hardware RAID 5 and Windows which eventually led me to ZFS on Linux which I've been using now for a while with spectacular results. It's designed from the ground up with data integrity in mind (up to triple parity bit stripes, self healing on the fly, 256 bit checksums per block of data, ditto blocks for metadata, all kinds of good stuff). Hopefully you have a backup of the data too.

---

### Post by tgalati4 on 2014-11-11
Are these "green" drives by any chance?

---

### Post by darkapec on 2014-11-12
I had a similar issue when I was using cheap drives. The raid ran fine for over a year then drives just starting falling out of sync and the raid was constantly rebuilding. I eventually ended up loosing all of my data. What kind of drives do you have? "[FONT=Ubuntu Mono]sudo lshw -c storage -c disk" [/FONT]will tell you the model number. I purchased several WD4000FYYZ drives and have never had an issue sense. 

I would suggest you track down "rubylaser" he is a member here on the forums. He is very VERY knowledgeable with mdadm. He helped me in the past when my raid 5 was failing.

---

### Post by RGee89 on 2014-11-12
Some are desktop drives. I think I'll have to swap them out for NAS drives. I have two WD Reds in there... I read up on ZFS and it seems pretty solid (thanks for the suggestion "lukeiamyourfather"), I will look into going that route (although I don't have ECC Ram). Maybe it's best to go back to the drawing board and come up with a better solution for my file server needs. I've been getting by with cheap desktop hardware so far, perhaps it's time to upgrade to server-grade hardware.

Here is my ```
lshw
``` below:

```

 *-scsi:0
     *-disk:0
          description: ATA Disk
          product: WDC WD20EFRX-68A
          vendor: Western Digital
     *-disk:1
          description: ATA Disk
          product: WDC WD20EFRX-68A
          vendor: Western Digital
     *-disk:2
          description: ATA Disk
          product: ST2000DL001-9VT1
          vendor: Seagate
  *-scsi:1
     *-disk:0
          description: ATA Disk
          product: SAMSUNG HD204UI
     *-disk:1
          description: ATA Disk
          product: SAMSUNG HD204UI
     *-disk:2
          description: ATA Disk
          product: ST2000DM001-9YN1
          vendor: Seagate
     *-disk:3
          description: ATA Disk
          product: ST2000DM001-9YN1
          vendor: Seagate

```

and my ```
syslog
``` below:

```
[Wed Nov 12 02:37:38 2014]          res 11/cf:00:00:00:00/00:00:00:d0:11/00 Emask 0x2 (HSM violation)[Wed Nov 12 02:37:38 2014] ata3.02: status: { ERR }
[Wed Nov 12 02:37:38 2014] ata3.02: error: { ICRC UNC ABRT }
[Wed Nov 12 02:37:38 2014] ata3.02: failed command: WRITE FPDMA QUEUED
[Wed Nov 12 02:37:38 2014] ata3.02: cmd 61/00:f0:80:c0:ff/04:00:ae:00:00/40 tag 30 ncq 524288 out
[Wed Nov 12 02:37:38 2014]          res 11/cf:00:00:00:00/00:00:00:e0:11/00 Emask 0x2 (HSM violation)
[Wed Nov 12 02:37:38 2014] ata3.02: status: { ERR }
[Wed Nov 12 02:37:38 2014] ata3.02: error: { ICRC UNC ABRT }
[Wed Nov 12 02:37:38 2014] ata3.15: failed to read PMP product ID (Emask=0x40)
[Wed Nov 12 02:37:38 2014] ata3.15: hard resetting link
[Wed Nov 12 02:37:41 2014] ata3.15: softreset failed (SRST command error)
[Wed Nov 12 02:37:41 2014] ata3.15: reset failed (errno=-5), retrying in 8 secs
[Wed Nov 12 02:37:48 2014] ata3.15: hard resetting link
[Wed Nov 12 02:37:51 2014] ata3.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[Wed Nov 12 02:37:51 2014] ata3.15: PMP revalidation failed (errno=-19)
[Wed Nov 12 02:37:51 2014] ata3.15: limiting SATA link speed to 1.5 Gbps
[Wed Nov 12 02:37:56 2014] ata3.15: hard resetting link
[Wed Nov 12 02:37:58 2014] ata3.15: SATA link up 1.5 Gbps (SStatus 113 SControl 10)
[Wed Nov 12 02:37:58 2014] ata3.00: hard resetting link
[Wed Nov 12 02:37:58 2014] ata3.00: link resume succeeded after 1 retries
[Wed Nov 12 02:37:58 2014] ata3.00: SATA link down (SStatus 0 SControl 310)
[Wed Nov 12 02:37:58 2014] ata3.01: hard resetting link
[Wed Nov 12 02:37:59 2014] ata3.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[Wed Nov 12 02:37:59 2014] ata3.02: hard resetting link
[Wed Nov 12 02:37:59 2014] ata3.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[Wed Nov 12 02:37:59 2014] ata3.03: hard resetting link
[Wed Nov 12 02:37:59 2014] ata3.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[Wed Nov 12 02:37:59 2014] ata3.04: hard resetting link
[Wed Nov 12 02:38:00 2014] ata3.04: SATA link down (SStatus 0 SControl 310)
[Wed Nov 12 02:38:00 2014] ata3.05: hard resetting link
[Wed Nov 12 02:38:00 2014] ata3.05: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[Wed Nov 12 02:38:00 2014] ata3.01: configured for UDMA/100
[Wed Nov 12 02:38:00 2014] ata3.02: configured for UDMA/100
[Wed Nov 12 02:38:00 2014] ata3.03: configured for UDMA/100
[Wed Nov 12 02:38:00 2014] ata3: EH complete



```

---

### Post by tgalati4 on 2014-11-13
RAID works best with server-grade hardware:  enterprise-class disk drives (3X the price), EEC RAM, high-performance RAID controller, decent motherboard and CPU, dual power supplies, etc.  Because of the large amount of data involved with typical RAID setups, the entire data path needs redundancy (EEC and power) to preserve data.  ZFS gives you an extra level with checksums and pool scrubbing, but the hardware needs to be robust for ZFS to work properly.

RAID is not a backup strategy.

---

### Post by rubylaser on 2014-11-13
Another option is to look at a solution like [SnapRAID]("http://snapraid.sourceforge.net/") + a pooling solution like mhddfs if you are using your array for bulk media storage.  I was a long time mdadm user and I've since converted to using either ZFS or SnapRAID for home storage.  I use ZFS for my constantly changing data (VM pool), but SnapRAID for everything else at home.  With SnapRAID, each disk stands alone (can be mounted by itself), it supports checksumming (prevent bitrot), you can add disks one at a time, and it has less demanding hardware requirements than ZFS.  ZFS is AWESOME, but I like the flexibility of SnapRAID for my data that doesn't change often (videos, documents, tv shows, pictures, etc.).  If you are interested in SnapRAID, I have a writeup in my signature.

---

