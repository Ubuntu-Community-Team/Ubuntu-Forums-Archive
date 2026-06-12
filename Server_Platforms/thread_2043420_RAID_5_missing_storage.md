---
title: "RAID 5 missing storage?"
date: 2012-08-16
forum: Server Platforms
---

### Post by azteka22 on 2012-08-16
Hello Guys,

I am a little bit confused and was wondering if you guys could shed some light on this issue or if I have set up my RAID 5 incorrectly.

I set up a RAID 5 using 4 Hard drives ( I had some old HDD's laying around so I decided to create a RAID and setup an FTP server for my house) and installed Ubuntu 12.04 LTS Server Edition last night. 

My harddrive sizes: 
SDA - 60GB
SDB - 80GB
SDC - 30GB
SDD - 40GB

So I thought that creating a RAID array I would get around 180GB - 190GB since I would loose some storage to SWAP space and to parity bits.

However, after I finished doing everything listed under the Ubuntu Advance Installation (RAID) I noticed that my RAID 5 (/dev/md1) only showed having 83.3GB of space? 

I used 3GB of space from every hard drive for SWAP space. 
so /dev/md0 has the correct amount of space - 9GB for SWAP:

sudo mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Wed Aug 15 23:06:07 2012
     Raid Level : raid5
     Array Size : 8781312 (8.37 GiB 8.99 GB)
  Used Dev Size : 2927104 (2.79 GiB 3.00 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Wed Aug 15 23:46:57 2012
          State : clean 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : Ubuntu-SRVR:0  (local to host Ubuntu-SRVR)
           UUID : 6f1c292f:7343a649:60a73f26:90ae9b22
         Events : 19

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1


HOWEVER, /dev/md1 which is my EXT4 filesystem it only shows it has 83.3 GB?? 

sudo mdadm -D /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Wed Aug 15 23:06:38 2012
     Raid Level : raid5
     Array Size : 81317376 (77.55 GiB 83.27 GB)
  Used Dev Size : 27105792 (25.85 GiB 27.76 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Thu Aug 16 13:40:49 2012
          State : clean 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : Ubuntu-SRVR:1  (local to host Ubuntu-SRVR)
           UUID : 14d76d51:1deb54ec:d9dc43c2:19e659d3
         Events : 22

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2
       2       8       34        2      active sync   /dev/sdc2
       3       8       50        3      active sync   /dev/sdd2


These are my disks used:

sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bbd1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     5859327     2928640   fd  Linux raid autodetect
/dev/sda2   *     5859328   117229567    55685120   fd  Linux raid autodetect

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000167eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     5859327     2928640   fd  Linux raid autodetect
/dev/sdb2   *     5859328   156301311    75220992   fd  Linux raid autodetect

Disk /dev/sdc: 30.8 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders, total 60074784 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006e84d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048     5859327     2928640   fd  Linux raid autodetect
/dev/sdc2   *     5859328    60073983    27107328   fd  Linux raid autodetect

Disk /dev/sdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eece1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048     5859327     2928640   fd  Linux raid autodetect
/dev/sdd2   *     5859328    78163967    36152320   fd  Linux raid autodetect

Disk /dev/md1: 83.3 GB, 83268993024 bytes
2 heads, 4 sectors/track, 20329344 cylinders, total 162634752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1572864 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md0: 8992 MB, 8992063488 bytes
2 heads, 4 sectors/track, 2195328 cylinders, total 17562624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1572864 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/sde: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00036ce1

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          62     7826383     3913161    c  W95 FAT32 (LBA)


Is this normal to loose so much space when creating a RAID 5 devices or did I create this RAID incorrectly?

Please advice.


Thanks in advance.

---

### Post by darkod on 2012-08-16
If I'm not mistaken, RAID uses disks/partitions with maximum size as the smallest of them. Since /dev/sdc is only 30GB, your array is the same as if created from 4 x 30GB disks.

RAID5 loses one disk to parity, so you have usable 3 x 30GB = 90GB. So, md1 of approx 83GB sounds about right.

---

### Post by azteka22 on 2012-08-16
hmm..I did not know that, but if that is the case it does make sense and thus my RAID is set up correctly. Thank you for your fast response and knowledge.

Is there anything that can be done to help get more storage? I mean I just lost like 100GB of space ha.. If I remove the 30GB drive from the array then I would only have 3 disks, smallest being 40GB and you said 1 disk is lost to parity so 40 x 2 = ~ 80GB again? =\

---

### Post by darkod on 2012-08-16
Unfortunately with that disk combination there is not much you can do.

You could use the rest of the bigger disks as non-raided partitions, software raid allows you this. For example, create the sdX1 partitions for swap like now, then create the sdX2 partitions up to 30GB size, and on the three disks you can use the rest of the space beyond the 30GB as single partitions.

---

### Post by azteka22 on 2012-08-16
I see... Ok, I will try that. 

Thank you for your time and getting this cleared up for me! :D

---

