---
title: "RAID 5 drive(s) failure???"
date: 2009-03-15
forum: Server Platforms
---

### Post by UncleAelfrich on 2009-03-15
I think I'm in trouble, but I thought I would ask.

I have a Ubuntua server running 8.04. My home directory is on a RAID 5 array using 4 partitions (on only 3 drives, I know, I shouldn't have done this). [ADDED INFORMATION]I should add that it is a RAID 5 array over LVM.

When I try to boot the server, I get a failed fsck message. I am able to boot through putty from another machine and here is the output I get from various commands

> /var/log/fsck
fsck.ext3: Unable to resolve &#8216;UUID=c453f2c6-468c-45c9-88fb-c4c47e7dd185
/dev/sda2: clean, 19/1835008 files, 101880/7329656 blocks
/dev/sdb1: clean, 18270/8544256 files, 387137/34156190 blocks
/dev/sda1: clean, 11689/3055616 files, 470270/12207384 blocks
fsck died with exit status 8


sudo mdadm &#8211;assemble &#8211;scan
mdadm: /dev/md0 assembled from 1 drive and 1 spare - not enough to start the array

sudo mdadm &#8211;query /dev/md0
/dev/md0: is an md device which is not active

sudo blkid
/dev/sda1: UUID=&#8221;c0e8aa21-dffc-4230-b6ac-f48cf8823e0" TYPE=&#8221;ext3" SEC_TYPE=&#8221;ext2"
/dev/sda2: UUID=&#8221;22ab21b1-4a9f-48d5-906a-a5377c8d95e0" SEC_TYPE=&#8221;ext2" TYPE=&#8221;ext3" 
/dev/sdb1: UUID=&#8221;09937db6-12b0-4baf-afd9-b9561dd67140" SEC_TYPE=&#8221;ext2" TYPE=&#8221;ext3" 
/dev/sdc1: UUID=&#8221;ce8beab8-a8d5-rcda-84ab-b3145e6f946e" TYPE=&#8221;ext3" SEC_TYPE=&#8221;ext2" 
/dev/sdc2: UUID=&#8221;7d32ff56-37bf-47dc-29ad-32a16aab633c&#8221; TYPE=&#8221;mdraid
/dev/sdd1:UUID=&#8221;7d32ff56-37bf-47dc-29ad-32a16aab633c&#8221; TYPE=&#8221;mdraid
/dev/sdb2: UUID=&#8221;7d32ff56-37bf-47dc-29ad-32a16aab633c&#8221; TYPE=&#8221;mdraid
/dev/sdb3: UUID=&#8221;7d32ff56-37bf-47dc-29ad-32a16aab633c&#8221; TYPE=&#8221;mdraid
/dev/sdc3: TYPE=&#8221;swap&#8221; UUID=&#8221;b677c5ad-935b-4812-ac8e-7cc0359f9581"

and then this

>  sudo fsck /dev/md0
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Invalid argument while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

bigbadjohn@bigboy7:/$ sudo mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
bigbadjohn@bigboy7:/$ sudo mdadm --examine /dev/sdc2
/dev/sdc2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 56ff327d:dc47bf37:a132ad29:3c63ab6a
  Creation Time : Fri Jul 18 22:32:19 2008
     Raid Level : raid5
  Used Dev Size : 244195904 (232.88 GiB 250.06 GB)
     Array Size : 488391808 (465.77 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Feb 27 08:59:04 2009
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 5ac155ac - correct
         Events : 0.171

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        2        0      active sync   /dev/sda2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
bigbadjohn@bigboy7:/$ sudo mdadm --examine /dev/sdb2
/dev/sdb2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 56ff327d:dc47bf37:a132ad29:3c63ab6a
  Creation Time : Fri Jul 18 22:32:19 2008
     Raid Level : raid5
  Used Dev Size : 244195904 (232.88 GiB 250.06 GB)
     Array Size : 488391808 (465.77 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Feb 27 08:20:38 2009
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1
       Checksum : 5ac14c6a - correct
         Events : 0.32

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       50        2      active sync

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       50        2      active sync
   3     3       8       51        3      spare
bigbadjohn@bigboy7:/$ sudo mdadm --examine /dev/sdb3
/dev/sdb3:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 56ff327d:dc47bf37:a132ad29:3c63ab6a
  Creation Time : Fri Jul 18 22:32:19 2008
     Raid Level : raid5
  Used Dev Size : 244195904 (232.88 GiB 250.06 GB)
     Array Size : 488391808 (465.77 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Feb 15 10:21:27 2009
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1
       Checksum : 5ab196b8 - correct
         Events : 0.32

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       51        3      spare

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       50        2      active sync
   3     3       8       51        3      spare
bigbadjohn@bigboy7:/$ sudo mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 56ff327d:dc47bf37:a132ad29:3c63ab6a
  Creation Time : Fri Jul 18 22:32:19 2008
     Raid Level : raid5
  Used Dev Size : 244195904 (232.88 GiB 250.06 GB)
     Array Size : 488391808 (465.77 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Feb 27 09:03:11 2009
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 5ac15779 - correct
         Events : 0.178

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       0        0        0      removed
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
bigbadjohn@bigboy7:/$ sudo e2fsck -b 8193 /dev/md0
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Device or resource busy while trying to open /dev/md0
Filesystem mounted or opened exclusively by another program?
bigbadjohn@bigboy7:/$


I do have a tape backup, but it is several weeks old.

Please HELP!!! I have already learned more about linux than I wanted to learn, but it keeps dragging me back in, sorta like Michael Corelone is Godfather 3.

---

### Post by mrsteveman1 on 2009-03-15
hmmm, I'm not sure if the striping of md-raid means you are out of luck or not. I suspect you are if the data on the disk with the 2 partitions is not retrievable, that would mean a loss of half of the data which RAID5 can't recover from.

Out of curiosity, why are the UUID for all 4 mdraid component devices the same? Isn't that supposed to be different for all of them?

---

### Post by hyper_ch on 2009-03-15
maybe this helps - my knowledge on raids is too limited - : [http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)

however, as others have pointed out countless times before:

a RAID is NOT a BACKUP.

---

### Post by Vegan on 2009-03-15
Software RAID is very risky. Better to pay for a hardware RAID solution and use that. Software RAID can fail while the hardware does not care about any OS on the array.

There are many low cost RAID cards for SCSI, SAS and SATA availabe but drivers for Linux may mor may not be available.

---

### Post by UncleAelfrich on 2009-03-16
I'm not sure why the UUID are the same. Could this be because I used LVM?

---

### Post by fjgaude on 2009-03-17
> **UncleAelfrich said:**
> I'm not sure why the UUID are the same. Could this be because I used LVM?

Drives in a mdadm array all have the same UUID. That's how the array is assembled using the UUID. This UUID is not the one you would use to mount the array.

When mounting an md array there's no need to use the mount UUID, just use the /dev/md[n] as it doesn't change as you add devices to the OS.

---

