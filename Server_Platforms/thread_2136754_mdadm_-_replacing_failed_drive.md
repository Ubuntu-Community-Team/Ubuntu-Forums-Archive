---
title: "mdadm - replacing failed drive"
date: 2013-04-18
forum: Server Platforms
---

### Post by kendallp on 2013-04-18
Hello,

A few days ago I received a SMART error on one of the drives in my raid so I removed the drive and had a replacement (it was still under warranty) sent to me.  Yesterday I attempted to add the new drive to the raid array and goofed up.  I believe my issue was with the partitioning of the new drive.

The raid array is raid5 and is made up of five 2 TB drives.  /dev/sdc is the drive that failed.  Last night the raid was working but missing the failed drive.  I partitioned the new drive and ran "mdadm --add /dev/md0 /dev/sdc".  The process ran and this morning when I checked the status it showed two failed drives and the raid no longer working.

Below is the current mdadm --detail:

```
#sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Apr 18 07:43:28 2013
          State : clean, FAILED
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 256K

           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
         Events : 0.63481

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       17        1      active sync   /dev/sdb1
       2       0        0        2      removed
       3       0        0        3      removed
       4       8       81        4      active sync   /dev/sdf1

       5       8        1        -      faulty spare   /dev/sda1
```

And the current fdisk -l:

```
#sudo fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa2a226e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00064ce9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907029167  1953513560   fd  Linux raid autodetect

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e80a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048      499711      248832   83  Linux
/dev/sdd2          501758   488396799   243947521    5  Extended
/dev/sdd5          501760   488396799   243947520   8e  Linux LVM

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc744f265

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  3907024064  1953512001   fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              64  3907029167  1953514552   fd  Linux raid autodetect

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x086bff60

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/md0: 8001.6 GB, 8001584889856 bytes
2 heads, 4 sectors/track, 1953511936 cylinders, total 15628095488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 262144 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/mapper/NAS-root: 245.6 GB, 245647802368 bytes
255 heads, 63 sectors/track, 29864 cylinders, total 479780864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/NAS-root doesn't contain a valid partition table

Disk /dev/mapper/NAS-swap_1: 4148 MB, 4148166656 bytes
255 heads, 63 sectors/track, 504 cylinders, total 8101888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/NAS-swap_1 doesn't contain a valid partition table
```

As you can see, the new drive (/dev/sdc) was not properly added to the raid and now /dev/sda is showing as "faulty spare".  Can I simply run the following to rebuild the array minus the missing disk and then attempt to add /dev/sdc again?

```
#mdadm --stop /dev/md0
#mdadm --assemble /dev/md0 /dev/sd[a,b,c,e,f]1
```


Thank you in advance,
-Kendall

---

### Post by rubylaser on 2013-04-18
Yes, that would be the easiest next step.  I would also verify each disk's SMART info while you are at it, and check dmesg for why the other disk got kicked out of the array.

---

### Post by darkod on 2013-04-18
Also note this: To be precise, you need to add /dev/sdc1, not /dev/sdc. I think you know this and you wrote in your post /dev/sdc just to say which disk you are adding, but it creates confusion since with mdadm you can add both partitions and whole disks. I think using partitions is usually better, like you are using it. Not whole disks.

---

### Post by kendallp on 2013-04-18
Thank you Rubylaser and Darkod.  Unfortunately, things did not go how I was hoping.  

I stopped the array and attempted to reassemble it:

```
#sudo mdadm --assemble /dev/md0 /dev/sd[a,b,c,e,f]1
mdadm: device 5 in /dev/md0 has wrong state in superblock, but /dev/sdc1 seems ok
mdadm: /dev/md0 assembled from 3 drives and 1 spare - not enough to start the array.
```

I believe my mistake was when adding the new drive I made the mistake you mentioned Darkod and added /dev/sdc and not /dev/sdc1.  Hopefully I have not compounded the issue.  I attempted to reassemble the raid with the four working drives:

```
#sudo mdadm --assemble --force /dev/md0 /dev/sd[a,b,e,f]1
mdadm: forcing event count in /dev/sda1(2) from 63438 upto 63491
mdadm: clearing FAULTY flag for device 0 in /dev/md0 for /dev/sda1
mdadm: Marking array /dev/md0 as 'clean'
mdadm: /dev/md0 assembled from 4 drives - not enough to start the array.
```

So I then tried to use the --scan option and confirmed I made the mistake Darkod mentioned:

```
#sudo mdadm --assemble --scan
mdadm: WARNING /dev/sdc1 and /dev/sdc appear to have very similar superblocks.
      If they are really different, please --zero the superblock on one
      If they are the same or overlap, please remove one from the
      DEVICE list in mdadm.conf.
kendall@NAS:~$ sudo mdadm --assemble /dev/md0 /dev/sd[a,b,c,e,f]1
mdadm: ignoring /dev/sdb1 as it reports /dev/sda1 as failed
mdadm: ignoring /dev/sdf1 as it reports /dev/sda1 as failed
mdadm: /dev/md0 assembled from 2 drives and 1 spare - not enough to start the array.
```

I'm not sure what my best option is from here.  Below is the output from --examine:

```
#sudo mdadm --misc --examine /dev/sd[abcef]1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Apr 18 00:13:41 2013
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : af870261 - correct
         Events : 63491

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     2       8        1        2      active sync   /dev/sda1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       32        5      spare   /dev/sdc
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Apr 18 20:43:29 2013
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 0
       Checksum : af8822b8 - correct
         Events : 63491

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
/dev/sdc1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Apr 18 07:31:35 2013
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : af87692e - correct
         Events : 63463

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     5       8       32        5      spare   /dev/sdc

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       32        5      spare   /dev/sdc
/dev/sde1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Apr 18 20:43:29 2013
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 0
       Checksum : af8822e2 - correct
         Events : 63491

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8       65        0      active sync   /dev/sde1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      active sync
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
/dev/sdf1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Apr 18 20:43:29 2013
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 0
       Checksum : af8822fe - correct
         Events : 63491

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     4       8       81        4      active sync   /dev/sdf1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
```

And finally (and unfortunately):

```
#sudo mdadm --misc --examine /dev/sdc
/dev/sdc:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Apr 18 07:31:35 2013
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : af87692e - correct
         Events : 63463

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     5       8       32        5      spare   /dev/sdc

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       32        5      spare   /dev/sdc
```


Thank you again in advance,
-Kendall

---

### Post by darkod on 2013-04-19
The counters on four partitions are identical, and on sdc1 is very similar. You should be able to force assemble this.

As for adding sdc by mistake, simply zero the superblock.
```
sudo mdadm --zero-superblock /dev/sdc
```

Your --examine details don't show Device Role, you will need the exact order to force assemble. Don't assume the order is abcef because it might not be. What does this command output:
```
sudo mdadm --examine /dev/sd[abcef]1
```

PS. Also I would comment out all ARRAY definitions in mdadm.conf since right now it can be confused what belongs where. It seems to think you have 6 members, so it says it can't start the array with 4 members. A 5 member raid5 should be able to start with 4 members present.

---

### Post by kendallp on 2013-04-19
Thank you Darko,

Below is the output you requested:

```
#sudo mdadm --examine /dev/sd[abcef]1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Apr 19 07:50:18 2013
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : af88befe - correct
         Events : 63503

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     2       8        1        2      active sync   /dev/sda1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Apr 19 07:50:18 2013
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : af88bf0c - correct
         Events : 63503

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
mdadm: No md superblock detected on /dev/sdc1.
/dev/sde1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Apr 19 07:50:18 2013
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : af88bf3a - correct
         Events : 63503

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8       65        0      active sync   /dev/sde1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
/dev/sdf1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Apr 19 07:50:18 2013
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : af88bf52 - correct
         Events : 63503

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     4       8       81        4      active sync   /dev/sdf1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
```


I tried to assemble (not using force) after zeroing out the superblock:

```
#sudo mdadm --assemble /dev/md0 /dev/sd[a,b,c,e,f]1
mdadm: no RAID superblock on /dev/sdc1
mdadm: /dev/sdc1 has no superblock - assembly aborted
```


So I then tried assembling with --scan:

```
#sudo mdadm --assemble --scan
mdadm: /dev/md0 has been started with 4 drives (out of 5).
```


Success.... well maybe not:

```
#sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Apr 18 20:43:29 2013
          State : clean, degraded
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 256K

           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
         Events : 0.63491

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       17        1      active sync   /dev/sdb1
       2       8        1        2      active sync   /dev/sda1
       3       0        0        3      removed
       4       8       81        4      active sync   /dev/sdf1
```


The array is now restarted but I cannot access any of the data.  Does that mean the drives are assembled out of order as you mentioned?


Thank you again,
-Kendall

---

### Post by darkod on 2013-04-19
It might be. Look at the Raid Device values, I think they should show the order. You are using metadata version 0.90 and I guess that's why there is no separate device Role enry that I expected.

But according to the Raid Device order, the order should be sde,sdb,sda,missing,sdf.

So, try assembling it with something like (and stop md0 if it's running right now):
```
sudo mdadm --stop /dev/md0
sudo mdadm --assemble /dev/md0 /dev/sde1 /dev/sdb1 /dev/sda1 missing /dev/sdf1
```

That should assemble it leaving one slot empty (missing) for the missing disk. If this works, you will add /dev/sdc1 later to this missing slot.

if that assembles, don't forget to mount it first, and see if the data is there. Then add sdc1.

---

### Post by kendallp on 2013-04-19
> **darkod said:**
> If that assembles, don't forget to mount it first, and see if the data is there. Then add sdc1.

This is the reason you should not work on computers prior to having coffee.  I remembered while taking a shower that I had not mounted the array.

So I have reassembled using --scan and mounted the raid.  Data all looks to be there.  I am going to now add /dev/sdc1 and if everything is working will marked this solved.


Thank you again Darko for all your help.


-Kendall

---

### Post by kendallp on 2013-04-20
No such luck.  Added /dev/sdc1 which took around 26 hours to finish.  Results from this morning:

```
#cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[5](S) sde1[0] sdf1[4] sda1[6](F) sdb1[1]
      7814047744 blocks level 5, 256k chunk, algorithm 2 [5/3] [UU__U]
```

```
#sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Apr 20 06:32:53 2013
          State : clean, FAILED
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 256K

           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
         Events : 0.63539

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       17        1      active sync   /dev/sdb1
       2       0        0        2      removed
       3       0        0        3      removed
       4       8       81        4      active sync   /dev/sdf1

       5       8       33        -      spare   /dev/sdc1
       6       8        1        -      faulty spare   /dev/sda1
```

```
#sudo mdadm --examine /dev/sd[abcef]1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Fri Apr 19 23:41:52 2013
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : af899e70 - correct
         Events : 63530

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     2       8        1        2      active sync   /dev/sda1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Sat Apr 20 10:02:39 2013
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : af8a3022 - correct
         Events : 63541

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Sat Apr 20 10:02:39 2013
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : af8a3034 - correct
         Events : 63541

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     5       8       33        5      spare   /dev/sdc1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
/dev/sde1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Sat Apr 20 10:02:39 2013
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : af8a3050 - correct
         Events : 63541

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8       65        0      active sync   /dev/sde1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
/dev/sdf1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Sat Apr 20 10:02:39 2013
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : af8a3068 - correct
         Events : 63541

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     4       8       81        4      active sync   /dev/sdf1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
```


Any suggestions from here?


Thank you,
-Kendall

---

### Post by kendallp on 2013-04-20
And in case it helps:

```
#cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 UUID=99f44a81:c204bc31:cced5de7:ca715931

# This file was auto-generated on Thu, 20 Dec 2012 20:33:25 -0500
# by mkconf $Id$
```


```
#sudo fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa2a226e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00064ce9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907029167  1953513560   fd  Linux raid autodetect

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e80a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048      499711      248832   83  Linux
/dev/sdd2          501758   488396799   243947521    5  Extended
/dev/sdd5          501760   488396799   243947520   8e  Linux LVM

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc744f265

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  3907024064  1953512001   fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              64  3907029167  1953514552   fd  Linux raid autodetect

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x086bff60

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/mapper/NAS-root: 245.6 GB, 245647802368 bytes
255 heads, 63 sectors/track, 29864 cylinders, total 479780864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/NAS-root doesn't contain a valid partition table

Disk /dev/mapper/NAS-swap_1: 4148 MB, 4148166656 bytes
255 heads, 63 sectors/track, 504 cylinders, total 8101888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/NAS-swap_1 doesn't contain a valid partition table

Disk /dev/md0: 8001.6 GB, 8001584889856 bytes
2 heads, 4 sectors/track, 1953511936 cylinders, total 15628095488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 262144 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
```


Thank you,
-Kendall

---

### Post by darkod on 2013-04-20
Are you sure sda1 is good? It was dropped from the array too. It then seems to be added as faulty spare, not only as spare, and taking slot 6 instead of slot 2 it had.

Looks to me like sda1 is failing too, making problems for you since one member has already failed.

When you did the --assemble --scan before adding sdc1, did you wait for all the sync to finish if necessary? Did you check that the array is fully working and active (degraded) with 4 members, before adding sdc1?

Not sure what's best. I also don't have idea why sdc1 was added in slot 5 instead of slot 3 that was empty.

In this situation I would probably try zeroing the superblock on sdc1 again, and then forcing the assemble of md0 with the 4 members (not with --scan, manually stating the members). Leaving the array to get fully working, check the --detail md0 again and see that all 4 members are marked active sync.
Only after that add sdc1. The problem is that if sda1 is also starting to fail, when it starts adding sdc1 and syncing, there will be lots of activity on the existing 4 members, making sda1 more probable to fail again before the full sync is done.

If you manage to get to the full sync with 5 members, you can consider replacing sda1 with a new disk.

I'll check if rubylaser can drop by and have a look, he knows much more about mdadm.

---

### Post by kendallp on 2013-04-20
Thank you Darko.  I stopped the array and attempted to reassemble with --scan:

```
#sudo mdadm --assemble --scan
mdadm: WARNING /dev/sdc1 and /dev/sdc appear to have very similar superblocks.
      If they are really different, please --zero the superblock on one
      If they are the same or overlap, please remove one from the
      DEVICE list in mdadm.conf.
```


So I zeroed out the superblock on /dev/sdc again without a problem and since the sync did not work attempted to zero out /dev/sdc1:

```
#sudo mdadm --zero-superblock /dev/sdc1
mdadm: Unrecognised md component device - /dev/sdc1
```


And tried to reassemble with --scan:

```
#sudo mdadm --assemble --scan
mdadm: /dev/md0 assembled from 3 drives - not enough to start the array.
```


I believe sda1 is a good drive, no SMART problems:

```
#sudo smartctl -Hc /dev/sda1
SMART overall-health self-assessment test result: PASSED
```


I also tried using missing:

```
#sudo mdadm --assemble /dev/md0 /dev/sde1 /dev/sdb1 /dev/sda1 missing /dev/sdf1
mdadm: cannot open device missing: No such file or directory
mdadm: missing has no superblock - assembly aborted
```


Thanks,
-Kendall

---

### Post by darkod on 2013-04-20
Hmmm, why does sdc have superblock again? I wonder if this is a result of using --scan or using the existing ARRAY definitions in mdadm.conf.

The latest --assemble you posted should have worked, maybe it also needed the --force option since the event counter on sda1 is not the same as on the others.

Try something like this:
1. Stop md0 if not already stopped.
2. Open mdadm.conf and comment out the md0 ARRAy definition (put the # symbol in front). Save and close the file.
3. Try to force the assemble manually without using --scan with:
```
sudo mdadm --assemble --force /dev/md0 /dev/sde1 /dev/sdb1 /dev/sda1 missing /dev/sdf1
```

If that assembles, check the current status with:
```
cat /proc/mdstat
```

It should not say syncing. If it does, wait for it to finish.

Lets see if you can get it working with four members first.

---

### Post by kendallp on 2013-04-20
It does not seem to like missing:

```
#sudo mdadm --assemble --force /dev/md0 /dev/sde1 /dev/sdb1 /dev/sda1 missing /dev/sdf1
mdadm: cannot open device missing: No such file or directory
mdadm: missing has no superblock - assembly aborted
```

---

### Post by rubylaser on 2013-04-20
Can you show the full smart output from /dev/sda?  Sometimes the passed isn't really a true indicator of the disk's health.

```
smartctl -a /dev/sda
```

and can I see your metadata again for each disk?
```
mdadm -E [COLOR=#000000][FONT=Ubuntu Mono]/dev/sd[abcdef]1[/FONT][/COLOR]
```

---

### Post by kendallp on 2013-04-20
Here you go and thank you:

```
#sudo smartctl -a /dev/sda
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-39-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital AV-GP
Device Model:     WDC WD20EVDS-63T3B0
Serial Number:    WD-WCAVY5574010
LU WWN Device Id: 5 0014ee 204fcd936
Firmware Version: 01.00A01
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Apr 20 13:22:00 2013 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (41580) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   151   142   021    Pre-fail  Always       -       9441
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       382
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       6457
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       315
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       36
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       767
194 Temperature_Celsius     0x0022   114   100   000    Old_age   Always       -       38
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   199   199   000    Old_age   Always       -       394
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       9
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   049   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%      6406         2276028002

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

---

### Post by rubylaser on 2013-04-20
The disk looks okay, but the read failure in it's logs are not good.  How about running a long test on it?
```
smartctl -t long /dev/sda
```

and, how about this too?
```
[COLOR=#000000][FONT=Ubuntu Mono]mdadm -E [/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono][FONT=Ubuntu Mono]/dev/sd[abcdef]1
```[/FONT][/FONT][/COLOR][/COLOR]

---

### Post by kendallp on 2013-04-20
SMART long is running and will finish at 6pm EST.  I'll update once it finishes (along with the metadata).  Thanks Rubylaser.


-Kendall

---

### Post by kendallp on 2013-04-20
Test results:

```
#sudo smartctl -l selftest /dev/sda
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-39-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      6458         2276028002
# 2  Short offline       Completed: read failure       90%      6406         2276028002
```

```
#sudo smartctl -a /dev/sda
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-39-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital AV-GP
Device Model:     WDC WD20EVDS-63T3B0
Serial Number:    WD-WCAVY5574010
LU WWN Device Id: 5 0014ee 204fcd936
Firmware Version: 01.00A01
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Apr 20 16:58:14 2013 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121) The previous self-test completed having
                                        the read element of the test failed.
Total time to complete Offline
data collection:                (41580) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   151   142   021    Pre-fail  Always       -       9441
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       382
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       6461
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       315
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       36
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       767
194 Temperature_Celsius     0x0022   111   100   000    Old_age   Always       -       41
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   199   199   000    Old_age   Always       -       394
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       9
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   049   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      6458         2276028002
# 2  Short offline       Completed: read failure       90%      6406         2276028002

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```


So it looks like there are some unreadable sectors but the drive is not failing.  Or am I misunderstanding the results?

Finally the metadata:

```
#sudo mdadm -E /dev/sd[abcdef]1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Fri Apr 19 23:41:52 2013
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : af899e70 - correct
         Events : 63530

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     2       8        1        2      active sync   /dev/sda1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sat Apr 20 11:28:21 2013
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 0
       Checksum : af8a440c - correct
         Events : 63547

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
mdadm: No md superblock detected on /dev/sdc1.
mdadm: No md superblock detected on /dev/sdd1.
/dev/sde1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sat Apr 20 11:28:21 2013
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 0
       Checksum : af8a443a - correct
         Events : 63547

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8       65        0      active sync   /dev/sde1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
/dev/sdf1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sat Apr 20 11:28:21 2013
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 0
       Checksum : af8a4452 - correct
         Events : 63547

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     4       8       81        4      active sync   /dev/sdf1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
```


Thank you again Rubylaser and Darko.


-Kendall

---

### Post by darkod on 2013-04-20
Strange, only the sda1 superblock shows it as member at slot 2. But the superblocks on other three partitions don't mention sda1. And have even counters little bit higher.

Wait for rubylaser's opinion, but to me it looks like you could try forced assemble with the four partitions, and later add sdc1. Not sure why it doesn't take the missing option, hope I'm not using the syntax wrong. The missing slot should be specified somehow, so that it knows not to expect a device there.

---

### Post by rubylaser on 2013-04-20
> **darkod said:**
> Strange, only the sda1 superblock shows it as member at slot 2. But the superblocks on other three partitions don't mention sda1. And have even counters little bit higher.

Wait for rubylaser's opinion, but to me it looks like you could try forced assemble with the four partitions, and later add sdc1. Not sure why it doesn't take the missing option, hope I'm not using the syntax wrong. The missing slot should be specified somehow, so that it knows not to expect a device there.

I would do exactly this.  Try to force assemble with sdc at this point.  You do have a number of bad sectors on sda, so I'd be thinking about replacing it soon.

---

### Post by kendallp on 2013-04-20
SDC does not seem to have resynced correctly.  Darko mentioned using "missing" but I received an error when trying to use it.

```
#sudo mdadm --assemble --force /dev/md0 /dev/sde1 /dev/sdb1 /dev/sda1 /dev/sdc1 /dev/sdf1
mdadm: no RAID superblock on /dev/sdc1
mdadm: /dev/sdc1 has no superblock - assembly aborted
```


Thank you,
-Kendall

---

### Post by rubylaser on 2013-04-21
> **kendallp said:**
> SDC does not seem to have resynced correctly.  Darko mentioned using "missing" but I received an error when trying to use it.

```
#sudo mdadm --assemble --force /dev/md0 /dev/sde1 /dev/sdb1 /dev/sda1 /dev/sdc1 /dev/sdf1
mdadm: no RAID superblock on /dev/sdc1
mdadm: /dev/sdc1 has no superblock - assembly aborted
```


Thank you,
-Kendall

Just try it like this.
```
mdadm --stop /dev/md0
mdadm --assemble --force /dev/md0 /dev/sd[abdef]1
```

---

### Post by darkod on 2013-04-21
rubylaser, sdd1 is not a member, that's the one disk outside the array. If the missing is not accepted, should it be like:
```
sudo mdadm --assemble --force /dev/md0 /dev/sd[abef]1
```

Also, is the order not important? Because the order is not abef.

And can the above work since it's a 5 member array and you are only giving it 4 members specified?

---

### Post by kendallp on 2013-04-21
After doing further reading on the interwebs, the order seems to be important for --create but not --assemble; as is "missing".  So I tried assembling with --force:

```
#sudo mdadm --assemble --force -v /dev/md0 /dev/sd[abef]1
mdadm: looking for devices for /dev/md0
mdadm: /dev/sda1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 4.
mdadm: forcing event count in /dev/sda1(2) from 63530 upto 63547
mdadm: clearing FAULTY flag for device 0 in /dev/md0 for /dev/sda1
mdadm: Marking array /dev/md0 as 'clean'
mdadm: added /dev/sdb1 to /dev/md0 as 1
mdadm: added /dev/sda1 to /dev/md0 as 2
mdadm: no uptodate device for slot 3 of /dev/md0
mdadm: added /dev/sdf1 to /dev/md0 as 4
mdadm: added /dev/sde1 to /dev/md0 as 0
mdadm: /dev/md0 assembled from 4 drives - not enough to start the array.
```

```
#sudo mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
```

```
#cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sde1[0](S) sdf1[4](S) sda1[2](S) sdb1[1](S)
      7814050240 blocks

unused devices: <none>
```

```
#sudo mdadm -E /dev/sd[abcef]1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Fri Apr 19 23:41:52 2013
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : af899e81 - correct
         Events : 63547

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     2       8        1        2      active sync   /dev/sda1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sat Apr 20 11:28:21 2013
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 0
       Checksum : af8a440c - correct
         Events : 63547

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
mdadm: No md superblock detected on /dev/sdc1.
/dev/sde1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sat Apr 20 11:28:21 2013
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 0
       Checksum : af8a4437 - correct
         Events : 63547

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8       65        0      active sync   /dev/sde1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      active sync
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
/dev/sdf1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sat Apr 20 11:28:21 2013
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 0
       Checksum : af8a4452 - correct
         Events : 63547

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     4       8       81        4      active sync   /dev/sdf1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
```


So I stopped /dev/md0 and tried assembling again with --scan:

```
#sudo mdadm --assemble --scan -v
mdadm: looking for devices for further assembly
mdadm: no recogniseable superblock on /dev/dm-1
mdadm: no recogniseable superblock on /dev/dm-0
mdadm: no RAID superblock on /dev/sdb
mdadm: no RAID superblock on /dev/sdf
mdadm: no RAID superblock on /dev/sde
mdadm: no RAID superblock on /dev/sdd5
mdadm: no RAID superblock on /dev/sdd2
mdadm: no RAID superblock on /dev/sdd1
mdadm: no RAID superblock on /dev/sdd
mdadm: no RAID superblock on /dev/sdc1
mdadm: no RAID superblock on /dev/sdc
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sdb1 is identified as a member of /dev/md/0, slot 1.
mdadm: /dev/sdf1 is identified as a member of /dev/md/0, slot 4.
mdadm: /dev/sde1 is identified as a member of /dev/md/0, slot 0.
mdadm: /dev/sda1 is identified as a member of /dev/md/0, slot 2.
mdadm: added /dev/sdb1 to /dev/md/0 as 1
mdadm: added /dev/sda1 to /dev/md/0 as 2
mdadm: no uptodate device for slot 3 of /dev/md/0
mdadm: added /dev/sdf1 to /dev/md/0 as 4
mdadm: added /dev/sde1 to /dev/md/0 as 0
mdadm: /dev/md/0 has been started with 4 drives (out of 5).
mdadm: looking for devices for further assembly
mdadm: looking for devices for further assembly
mdadm: no recogniseable superblock on /dev/md/0
mdadm: no recogniseable superblock on /dev/dm-1
mdadm: no recogniseable superblock on /dev/dm-0
mdadm: /dev/sdb1 is busy - skipping
mdadm: Cannot assemble mbr metadata on /dev/sdb
mdadm: /dev/sdf1 is busy - skipping
mdadm: Cannot assemble mbr metadata on /dev/sdf
mdadm: /dev/sde1 is busy - skipping
mdadm: Cannot assemble mbr metadata on /dev/sde
mdadm: no recogniseable superblock on /dev/sdd5
mdadm: Cannot assemble mbr metadata on /dev/sdd2
mdadm: no recogniseable superblock on /dev/sdd1
mdadm: Cannot assemble mbr metadata on /dev/sdd
mdadm: no recogniseable superblock on /dev/sdc1
mdadm: Cannot assemble mbr metadata on /dev/sdc
mdadm: /dev/sda1 is busy - skipping
mdadm: Cannot assemble mbr metadata on /dev/sda
```


Array back up and I'm back to where I was before when trying to --add /dev/sdc1:

```
#sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Apr 20 11:28:21 2013
          State : clean, degraded
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 256K

           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
         Events : 0.63547

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       17        1      active sync   /dev/sdb1
       2       8        1        2      active sync   /dev/sda1
       3       0        0        3      removed
       4       8       81        4      active sync   /dev/sdf1
```

```
#sudo mdadm -E /dev/sd[abcef]1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Apr 21 13:32:00 2013
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : af8bb270 - correct
         Events : 63549

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     2       8        1        2      active sync   /dev/sda1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Apr 21 13:32:00 2013
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : af8bb27e - correct
         Events : 63549

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
mdadm: No md superblock detected on /dev/sdc1.
/dev/sde1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Apr 21 13:32:00 2013
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : af8bb2ac - correct
         Events : 63549

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8       65        0      active sync   /dev/sde1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
/dev/sdf1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Apr 21 13:32:00 2013
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : af8bb2c4 - correct
         Events : 63549

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     4       8       81        4      active sync   /dev/sdf1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
```


Checking filesystem:

```
#sudo fsck -fn /dev/md0
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
Warning: skipping journal recovery because doing a read-only filesystem check.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong (200993995, counted=200994014).
Fix? no

Free inodes count wrong (488335202, counted=488335203).
Fix? no


/dev/md0: ********** WARNING: Filesystem still has errors **********

/dev/md0: 47262/488382464 files (36.0% non-contiguous), 1752517941/1953511936 blocks
```


Should I let fsck repair the blocks and inodes prior to trying to readd /dev/sdc1?


Thanks again,
-Kendall

---

### Post by darkod on 2013-04-21
I would let it repair. And then check with cat /proc/mdstat again if the array is assembled and the disks are not still syncing.

If there is no syncing going on, it should be safe to add sdc1.

---

### Post by rubylaser on 2013-04-21
> **darkod said:**
> rubylaser, sdd1 is not a member, that's the one disk outside the array. If the missing is not accepted, should it be like:
```
sudo mdadm --assemble --force /dev/md0 /dev/sd[abef]1
```

Also, is the order not important? Because the order is not abef.

And can the above work since it's a 5 member array and you are only giving it 4 members specified?

As said above, the order is not important on an assemble only on a re-create.  mdadm can see the metadata and can assemble. Also, yes, it can assemble an array given only 4 of the 5 devices.  Good catch on the the /dev/sdd1 not being a member :)

Also, I hope you have a backup because the fsck, although necessary at this point, is likely to leave you with a bunch of orphaned inodes (they will show up in lost+found).  Please let us know how that goes.

---

### Post by kendallp on 2013-04-21
Fingers crossed we are going to work from here:

fsck finished:

```
#sudo fsck /dev/md0
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
/dev/md0: recovering journal
/dev/md0 has been mounted 319 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong (200993995, counted=200994014).
Fix<y>? yes

Free inodes count wrong (488335202, counted=488335203).
Fix<y>? yes


/dev/md0: ***** FILE SYSTEM WAS MODIFIED *****
/dev/md0: 47261/488382464 files (36.0% non-contiguous), 1752517922/1953511936 blocks
```


Raid seems to be up, running, and synced; minus /dev/sdc1 which should go in slot 3:

```
#sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Apr 21 15:04:38 2013
          State : clean, degraded
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 256K

           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
         Events : 0.63555

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       17        1      active sync   /dev/sdb1
       2       8        1        2      active sync   /dev/sda1
       3       0        0        3      removed
       4       8       81        4      active sync   /dev/sdf1
```

```
#cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sde1[0] sdf1[4] sda1[2] sdb1[1]
      7814047744 blocks level 5, 256k chunk, algorithm 2 [5/4] [UUU_U]

unused devices: <none>
```


And finally drive information:

```
#sudo fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa2a226e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
63 heads, 63 sectors/track, 984386 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00064ce9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907029167  1953513560   fd  Linux raid autodetect

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e80a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048      499711      248832   83  Linux
/dev/sdd2          501758   488396799   243947521    5  Extended
/dev/sdd5          501760   488396799   243947520   8e  Linux LVM

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc744f265

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  3907024064  1953512001   fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              64  3907029167  1953514552   fd  Linux raid autodetect

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x086bff60

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/mapper/NAS-root: 245.6 GB, 245647802368 bytes
255 heads, 63 sectors/track, 29864 cylinders, total 479780864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/NAS-root doesn't contain a valid partition table

Disk /dev/mapper/NAS-swap_1: 4148 MB, 4148166656 bytes
255 heads, 63 sectors/track, 504 cylinders, total 8101888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/NAS-swap_1 doesn't contain a valid partition table

Disk /dev/md0: 8001.6 GB, 8001584889856 bytes
2 heads, 4 sectors/track, 1953511936 cylinders, total 15628095488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 262144 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
```


Here we go:

```
#sudo mdadm --add /dev/md0 /dev/sdc1
mdadm: added /dev/sdc1
```

```
#sudo cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[5] sde1[0] sdf1[4] sda1[2] sdb1[1]
      7814047744 blocks level 5, 256k chunk, algorithm 2 [5/4] [UUU_U]
      [>....................]  recovery =  0.0% (762560/1953511936) finish=1365.7min speed=23830K/sec

unused devices: <none>
```


I'll followup tomorrow once it has finished syncing but I don't think this will work.  sdc1 is being put in slot 5 not 3.


-Kendall

---

### Post by rubylaser on 2013-04-21
Did you try to mount the array, to verify that your data is intact?  That's really more important than adding /dev/sdc1 at this point.  The fsck actually looked very good, only 1 inode error is great :)

---

### Post by kendallp on 2013-04-21
> **rubylaser said:**
> Did you try to mount the array, to verify that your data is intact?  That's really more important than adding /dev/sdc1 at this point.  The fsck actually looked very good, only 1 inode error is great :)

I did not this time but the previous time I had the array up with 4 of 5 disks I mounted it and the data looked good.

---

### Post by kendallp on 2013-04-22
The --add failed again.  /dev/sda looks to be dying also as you mentioned Rubylaser:

```
#cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[5](S) sde1[0] sdf1[4] sda1[6](F) sdb1[1]
      7814047744 blocks level 5, 256k chunk, algorithm 2 [5/3] [UU__U]

unused devices: <none>
```

```
#dmesg
[319663.817798] md: md0 stopped.
[319663.822377] md: bind<sdb1>
[319663.822700] md: bind<sda1>
[319663.825121] md: bind<sdf1>
[319663.825454] md: bind<sde1>
[319663.993858] md/raid:md0: device sde1 operational as raid disk 0
[319663.993864] md/raid:md0: device sdf1 operational as raid disk 4
[319663.993868] md/raid:md0: device sda1 operational as raid disk 2
[319663.993872] md/raid:md0: device sdb1 operational as raid disk 1
[319663.994233] md/raid:md0: allocated 5332kB
[319663.994342] md/raid:md0: raid level 5 active with 4 out of 5 devices, algorithm 2
[319663.994348] RAID conf printout:
[319663.994352]  --- level:5 rd:5 wd:4
[319663.994356]  disk 0, o:1, dev:sde1
[319663.994361]  disk 1, o:1, dev:sdb1
[319663.994364]  disk 2, o:1, dev:sda1
[319663.994367]  disk 4, o:1, dev:sdf1
[319663.994421] md0: detected capacity change from 0 to 8001584889856
[319663.995135]  md0: unknown partition table
[327085.248505]  sdc: sdc1
[327169.852670] md: bind<sdc1>
[327170.269367] RAID conf printout:
[327170.269370]  --- level:5 rd:5 wd:4
[327170.269372]  disk 0, o:1, dev:sde1
[327170.269374]  disk 1, o:1, dev:sdb1
[327170.269376]  disk 2, o:1, dev:sda1
[327170.269378]  disk 3, o:1, dev:sdc1
[327170.269380]  disk 4, o:1, dev:sdf1
[327170.270003] md: recovery of RAID array md0
[327170.270005] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[327170.270007] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for recovery.
[327170.270011] md: using 128k window, over a total of 1953511936k.
[382470.075682] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[382470.075687] ata2.00: BMDMA stat 0x5
[382470.075692] ata2.00: failed command: READ DMA EXT
[382470.075700] ata2.00: cmd 25/00:28:97:55:a9/00:03:87:00:00/e0 tag 0 dma 413696 in
[382470.075702]          res 51/40:57:62:58:a9/40:00:87:00:00/e0 Emask 0x9 (media error)
[382470.075706] ata2.00: status: { DRDY ERR }
[382470.075709] ata2.00: error: { UNC }
[382470.154416] ata2.00: configured for UDMA/133
[382470.162495] ata2.01: configured for UDMA/133
[382470.162641] ata2: EH complete
[382474.076375] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[382474.076381] ata2.00: BMDMA stat 0x5
[382474.076385] ata2.00: failed command: READ DMA EXT
[382474.076393] ata2.00: cmd 25/00:28:97:55:a9/00:03:87:00:00/e0 tag 0 dma 413696 in
[382474.076395]          res 51/40:57:62:58:a9/40:00:87:00:00/e0 Emask 0x9 (media error)
[382474.076399] ata2.00: status: { DRDY ERR }
[382474.076402] ata2.00: error: { UNC }
[382474.092212] ata2.00: configured for UDMA/133
[382474.100182] ata2.01: configured for UDMA/133
[382474.100324] ata2: EH complete
[382477.722590] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[382477.722596] ata2.00: BMDMA stat 0x5
[382477.722600] ata2.00: failed command: READ DMA EXT
[382477.722608] ata2.00: cmd 25/00:28:97:55:a9/00:03:87:00:00/e0 tag 0 dma 413696 in
[382477.722610]          res 51/40:57:62:58:a9/40:00:87:00:00/e0 Emask 0x9 (media error)
[382477.722805] ata2.00: status: { DRDY ERR }
[382477.722807] ata2.00: error: { UNC }
[382477.738438] ata2.00: configured for UDMA/133
[382477.746409] ata2.01: configured for UDMA/133
[382477.746551] ata2: EH complete
[382480.791716] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[382480.791721] ata2.00: BMDMA stat 0x5
[382480.791725] ata2.00: failed command: READ DMA EXT
[382480.791733] ata2.00: cmd 25/00:28:97:55:a9/00:03:87:00:00/e0 tag 0 dma 413696 in
[382480.791735]          res 51/40:57:62:58:a9/40:00:87:00:00/e0 Emask 0x9 (media error)
[382480.791739] ata2.00: status: { DRDY ERR }
[382480.791742] ata2.00: error: { UNC }
[382480.805555] ata2.00: configured for UDMA/133
[382480.813545] ata2.01: configured for UDMA/133
[382480.813696] ata2: EH complete
[382483.905825] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[382483.905830] ata2.00: BMDMA stat 0x5
[382483.905834] ata2.00: failed command: READ DMA EXT
[382483.905843] ata2.00: cmd 25/00:28:97:55:a9/00:03:87:00:00/e0 tag 0 dma 413696 in
[382483.905844]          res 51/40:57:62:58:a9/40:00:87:00:00/e0 Emask 0x9 (media error)
[382483.905849] ata2.00: status: { DRDY ERR }
[382483.905851] ata2.00: error: { UNC }
[382483.920611] ata2.00: configured for UDMA/133
[382483.928610] ata2.01: configured for UDMA/133
[382483.928762] ata2: EH complete
[382487.142671] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[382487.142676] ata2.00: BMDMA stat 0x5
[382487.142681] ata2.00: failed command: READ DMA EXT
[382487.142689] ata2.00: cmd 25/00:28:97:55:a9/00:03:87:00:00/e0 tag 0 dma 413696 in
[382487.142690]          res 51/40:57:62:58:a9/40:00:87:00:00/e0 Emask 0x9 (media error)
[382487.142695] ata2.00: status: { DRDY ERR }
[382487.142697] ata2.00: error: { UNC }
[382487.156490] ata2.00: configured for UDMA/133
[382487.164470] ata2.01: configured for UDMA/133
[382487.164659] sd 1:0:0:0: [sda] Unhandled sense code
[382487.164662] sd 1:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[382487.164665] sd 1:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[382487.164669] Descriptor sense data with sense descriptors (in hex):
[382487.164671]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[382487.164678]         87 a9 58 62
[382487.164681] sd 1:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[382487.164686] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 87 a9 55 97 00 03 28 00
[382487.164693] end_request: I/O error, dev sda, sector 2276022370
[382487.164698] raid5_end_read_request: 68 callbacks suppressed
[382487.164700] md/raid:md0: read error not correctable (sector 2276022304 on sda1).
[382487.164703] md/raid:md0: Disk failure on sda1, disabling device.
[382487.164704] md/raid:md0: Operation continuing on 3 devices.
[382487.164755] md/raid:md0: read error not correctable (sector 2276022312 on sda1).
[382487.164758] md/raid:md0: read error not correctable (sector 2276022320 on sda1).
[382487.164760] md/raid:md0: read error not correctable (sector 2276022328 on sda1).
[382487.164762] md/raid:md0: read error not correctable (sector 2276022336 on sda1).
[382487.164764] md/raid:md0: read error not correctable (sector 2276022344 on sda1).
[382487.164766] md/raid:md0: read error not correctable (sector 2276022352 on sda1).
[382487.164769] md/raid:md0: read error not correctable (sector 2276022360 on sda1).
[382487.164771] md/raid:md0: read error not correctable (sector 2276022368 on sda1).
[382487.164773] md/raid:md0: read error not correctable (sector 2276022376 on sda1).
[382487.164785] ata2: EH complete
[382487.578038] md: md0: recovery done.
[382489.694569] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[382489.694575] ata2.00: BMDMA stat 0x5
[382489.694579] ata2.00: failed command: READ DMA EXT
[382489.694587] ata2.00: cmd 25/00:08:bf:58:a9/00:03:87:00:00/e0 tag 0 dma 397312 in
[382489.694589]          res 51/40:a7:19:5b:a9/40:00:87:00:00/e0 Emask 0x9 (media error)
[382489.694593] ata2.00: status: { DRDY ERR }
[382489.694596] ata2.00: error: { UNC }
[382489.709495] ata2.00: configured for UDMA/133
[382489.717388] ata2.01: configured for UDMA/133
[382489.717529] ata2: EH complete
[382492.210554] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[382492.210560] ata2.00: BMDMA stat 0x5
[382492.210564] ata2.00: failed command: READ DMA EXT
[382492.210572] ata2.00: cmd 25/00:08:bf:58:a9/00:03:87:00:00/e0 tag 0 dma 397312 in
[382492.210574]          res 51/40:a7:19:5b:a9/40:00:87:00:00/e0 Emask 0x9 (media error)
[382492.210578] ata2.00: status: { DRDY ERR }
[382492.210581] ata2.00: error: { UNC }
[382492.226482] ata2.00: configured for UDMA/133
[382492.234425] ata2.01: configured for UDMA/133
[382492.234557] ata2: EH complete
[382494.726601] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[382494.726606] ata2.00: BMDMA stat 0x5
[382494.726611] ata2.00: failed command: READ DMA EXT
[382494.726619] ata2.00: cmd 25/00:08:bf:58:a9/00:03:87:00:00/e0 tag 0 dma 397312 in
[382494.726621]          res 51/40:a7:19:5b:a9/40:00:87:00:00/e0 Emask 0x9 (media error)
[382494.726625] ata2.00: status: { DRDY ERR }
[382494.726628] ata2.00: error: { UNC }
[382494.743506] ata2.00: configured for UDMA/133
[382494.751405] ata2.01: configured for UDMA/133
[382494.751540] ata2: EH complete
[382497.264564] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[382497.264571] ata2.00: BMDMA stat 0x5
[382497.264576] ata2.00: failed command: READ DMA EXT
[382497.264586] ata2.00: cmd 25/00:08:bf:58:a9/00:03:87:00:00/e0 tag 0 dma 397312 in
[382497.264588]          res 51/40:a7:19:5b:a9/40:00:87:00:00/e0 Emask 0x9 (media error)
[382497.264593] ata2.00: status: { DRDY ERR }
[382497.264596] ata2.00: error: { UNC }
[382497.280500] ata2.00: configured for UDMA/133
[382497.288418] ata2.01: configured for UDMA/133
[382497.288549] ata2: EH complete
[382499.779570] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[382499.779575] ata2.00: BMDMA stat 0x5
[382499.779580] ata2.00: failed command: READ DMA EXT
[382499.779588] ata2.00: cmd 25/00:08:bf:58:a9/00:03:87:00:00/e0 tag 0 dma 397312 in
[382499.779589]          res 51/40:a7:19:5b:a9/40:00:87:00:00/e0 Emask 0x9 (media error)
[382499.779594] ata2.00: status: { DRDY ERR }
[382499.779596] ata2.00: error: { UNC }
[382499.793481] ata2.00: configured for UDMA/133
[382499.809419] ata2.01: configured for UDMA/133
[382499.809563] ata2: EH complete
[382502.295624] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[382502.295629] ata2.00: BMDMA stat 0x5
[382502.295633] ata2.00: failed command: READ DMA EXT
[382502.295641] ata2.00: cmd 25/00:08:bf:58:a9/00:03:87:00:00/e0 tag 0 dma 397312 in
[382502.295643]          res 51/40:a7:19:5b:a9/40:00:87:00:00/e0 Emask 0x9 (media error)
[382502.295647] ata2.00: status: { DRDY ERR }
[382502.295650] ata2.00: error: { UNC }
[382502.310536] ata2.00: configured for UDMA/133
[382502.318440] ata2.01: configured for UDMA/133
[382502.318612] sd 1:0:0:0: [sda] Unhandled sense code
[382502.318614] sd 1:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[382502.318616] sd 1:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[382502.318619] Descriptor sense data with sense descriptors (in hex):
[382502.318620]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[382502.318626]         87 a9 5b 19
[382502.318628] sd 1:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[382502.318632] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 87 a9 58 bf 00 03 08 00
[382502.318639] end_request: I/O error, dev sda, sector 2276023065
[382502.318643] raid5_end_read_request: 2 callbacks suppressed
[382502.318645] md/raid:md0: read error not correctable (sector 2276023000 on sda1).
[382502.318648] md/raid:md0: read error not correctable (sector 2276023008 on sda1).
[382502.318651] md/raid:md0: read error not correctable (sector 2276023016 on sda1).
[382502.318654] md/raid:md0: read error not correctable (sector 2276023024 on sda1).
[382502.318657] md/raid:md0: read error not correctable (sector 2276023032 on sda1).
[382502.318660] md/raid:md0: read error not correctable (sector 2276023040 on sda1).
[382502.318663] md/raid:md0: read error not correctable (sector 2276023048 on sda1).
[382502.318665] md/raid:md0: read error not correctable (sector 2276023056 on sda1).
[382502.318668] md/raid:md0: read error not correctable (sector 2276023064 on sda1).
[382502.318671] md/raid:md0: read error not correctable (sector 2276023072 on sda1).
[382502.318698] ata2: EH complete
[382502.727856] RAID conf printout:
[382502.727862]  --- level:5 rd:5 wd:3
[382502.727866]  disk 0, o:1, dev:sde1
[382502.727870]  disk 1, o:1, dev:sdb1
[382502.727874]  disk 2, o:0, dev:sda1
[382502.727877]  disk 3, o:1, dev:sdc1
[382502.727880]  disk 4, o:1, dev:sdf1
[382502.729666] RAID conf printout:
[382502.729668]  --- level:5 rd:5 wd:3
[382502.729670]  disk 0, o:1, dev:sde1
[382502.729671]  disk 1, o:1, dev:sdb1
[382502.729672]  disk 2, o:0, dev:sda1
[382502.729674]  disk 4, o:1, dev:sdf1
[382502.729677] RAID conf printout:
[382502.729678]  --- level:5 rd:5 wd:3
[382502.729685]  disk 0, o:1, dev:sde1
[382502.729687]  disk 1, o:1, dev:sdb1
[382502.729690]  disk 2, o:0, dev:sda1
[382502.729693]  disk 4, o:1, dev:sdf1
[382502.729751] RAID conf printout:
[382502.729756]  --- level:5 rd:5 wd:3
[382502.729759]  disk 0, o:1, dev:sde1
[382502.729762]  disk 1, o:1, dev:sdb1
[382502.729765]  disk 4, o:1, dev:sdf1
```


But it looks like /dev/sdc1 has been synced (though in slot 5 and not 3 where it should be):

```
#sudo mdadm -E /dev/sd[abcef]1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Mon Apr 22 06:29:13 2013
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : af8ca135 - correct
         Events : 63568

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     2       8        1        2      active sync   /dev/sda1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Mon Apr 22 07:00:34 2013
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : af8ca8b1 - correct
         Events : 63571

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Mon Apr 22 07:00:34 2013
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : af8ca8c3 - correct
         Events : 63571

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     5       8       33        5      spare   /dev/sdc1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
/dev/sde1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Mon Apr 22 07:00:34 2013
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : af8ca8df - correct
         Events : 63571

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8       65        0      active sync   /dev/sde1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
/dev/sdf1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 99f44a81:c204bc31:cced5de7:ca715931 (local to host NAS)
  Creation Time : Fri Dec 31 17:20:12 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Mon Apr 22 07:00:34 2013
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : af8ca8f7 - correct
         Events : 63571

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     4       8       81        4      active sync   /dev/sdf1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
```


So I thought I should be able to stop the array and reassemble:

```
#sudo mdadm --assemble --force -v /dev/md0 /dev/sd[abcef]1
mdadm: looking for devices for /dev/md0
mdadm: /dev/sda1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 5.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 4.
mdadm: forcing event count in /dev/sda1(2) from 63568 upto 63571
mdadm: clearing FAULTY flag for device 0 in /dev/md0 for /dev/sda1
mdadm: Marking array /dev/md0 as 'clean'
mdadm: added /dev/sdb1 to /dev/md0 as 1
mdadm: added /dev/sda1 to /dev/md0 as 2
mdadm: no uptodate device for slot 3 of /dev/md0
mdadm: added /dev/sdf1 to /dev/md0 as 4
mdadm: added /dev/sdc1 to /dev/md0 as 5
mdadm: added /dev/sde1 to /dev/md0 as 0
mdadm: /dev/md0 assembled from 4 drives and 1 spare - not enough to start the array.
```

```
sudo cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sde1[0](S) sdc1[5](S) sdf1[4](S) sda1[2](S) sdb1[1](S)
      9767563712 blocks

unused devices: <none>
```


So what if I stopped and tried --scan:

```
#sudo mdadm --assemble --scan -v
mdadm: looking for devices for further assembly
mdadm: no recogniseable superblock on /dev/dm-1
mdadm: no recogniseable superblock on /dev/dm-0
mdadm: no RAID superblock on /dev/sdb
mdadm: no RAID superblock on /dev/sdf
mdadm: no RAID superblock on /dev/sde
mdadm: no RAID superblock on /dev/sdd5
mdadm: no RAID superblock on /dev/sdd2
mdadm: no RAID superblock on /dev/sdd1
mdadm: no RAID superblock on /dev/sdd
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sdb1 is identified as a member of /dev/md/0, slot 1.
mdadm: /dev/sdf1 is identified as a member of /dev/md/0, slot 4.
mdadm: /dev/sde1 is identified as a member of /dev/md/0, slot 0.
mdadm: /dev/sdc1 is identified as a member of /dev/md/0, slot 5.
mdadm: /dev/sdc is identified as a member of /dev/md/0, slot 5.
mdadm: WARNING /dev/sdc1 and /dev/sdc appear to have very similar superblocks.
      If they are really different, please --zero the superblock on one
      If they are the same or overlap, please remove one from the
      DEVICE list in mdadm.conf.
mdadm: looking for devices for further assembly
mdadm: No arrays found in config file or automatically
```


Still getting the issue with /dev/sdc and /dev/sdc1 having similar superblocks even though I have zeroed /dev/sdc twice now.  And the array was commented out of the mdadm.conf prior to assembling yesterday:

```
#cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
#ARRAY /dev/md0 UUID=99f44a81:c204bc31:cced5de7:ca715931

# This file was auto-generated on Thu, 20 Dec 2012 20:33:25 -0500
# by mkconf $Id$
```


Any suggestions on how I can get sdc1 working so I can replace sda1?


Thank you again,
-Kendall

---

### Post by kendallp on 2013-04-22
Next I tried zeroing the superblock on every drive and recreating the array:

```
#sudo mdadm --create /dev/md0 --level=5 --raid-devices=5 --chunk=256 --metadata=0.90 /dev/sde1 /dev/sdb1 /dev/sda1 missing /dev/sdf1
```


Back up and running with 4 of 5 drives:

```
#cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdf1[4] sda1[2] sdb1[1] sde1[0]
      7814047744 blocks level 5, 256k chunk, algorithm 2 [5/4] [UUU_U]

unused devices: <none>
```

```
#sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Apr 22 22:04:15 2013
          State : clean, degraded
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 256K

           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
         Events : 0.21

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       17        1      active sync   /dev/sdb1
       2       8        1        2      active sync   /dev/sda1
       3       0        0        3      removed
       4       8       81        4      active sync   /dev/sdf1
```

```
#sudo mdadm -E /dev/sd[abcef]1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Apr 22 22:10:44 2013
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 6230a1c2 - correct
         Events : 23

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     2       8        1        2      active sync   /dev/sda1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Apr 22 22:10:44 2013
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 6230a1d0 - correct
         Events : 23

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
mdadm: No md superblock detected on /dev/sdc1.
/dev/sde1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Apr 22 22:10:44 2013
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 6230a1fe - correct
         Events : 23

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8       65        0      active sync   /dev/sde1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
/dev/sdf1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Apr 22 22:10:44 2013
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 6230a216 - correct
         Events : 23

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     4       8       81        4      active sync   /dev/sdf1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
```

```
#sudo fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa2a226e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
63 heads, 63 sectors/track, 984386 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00064ce9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907029167  1953513560   fd  Linux raid autodetect

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e80a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048      499711      248832   83  Linux
/dev/sdd2          501758   488396799   243947521    5  Extended
/dev/sdd5          501760   488396799   243947520   8e  Linux LVM

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc744f265

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  3907024064  1953512001   fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              64  3907029167  1953514552   fd  Linux raid autodetect

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x086bff60

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/mapper/NAS-root: 245.6 GB, 245647802368 bytes
255 heads, 63 sectors/track, 29864 cylinders, total 479780864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/NAS-root doesn't contain a valid partition table

Disk /dev/mapper/NAS-swap_1: 4148 MB, 4148166656 bytes
255 heads, 63 sectors/track, 504 cylinders, total 8101888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/NAS-swap_1 doesn't contain a valid partition table

Disk /dev/md0: 8001.6 GB, 8001584889856 bytes
2 heads, 4 sectors/track, 1953511936 cylinders, total 15628095488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 262144 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
```



Lots of errors when I checked the filesystem with fsck but repaired them all.  Once it was finished, I mounted the raid and I can see my data (I am sure some of it is corrupted but if I can save the majority this will be a win).

Finally, with fingers crossed, lets try and add /dev/sdc1 to get all 5 drives back in the array:

```
#sudo mdadm --add /dev/md0 /dev/sdc1
mdadm: added /dev/sdc1
```

```
#cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[5] sdf1[4] sda1[2] sdb1[1] sde1[0]
      7814047744 blocks level 5, 256k chunk, algorithm 2 [5/4] [UUU_U]
      [>....................]  recovery =  0.0% (592912/1953511936) finish=1427.2min speed=22804K/sec
```

```
#sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Apr 22 22:19:13 2013
          State : clean, degraded, recovering
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 256K

 Rebuild Status : 0% complete

           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
         Events : 0.25

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       17        1      active sync   /dev/sdb1
       2       8        1        2      active sync   /dev/sda1
       5       8       33        3      spare rebuilding   /dev/sdc1
       4       8       81        4      active sync   /dev/sdf1
```


Well, crap.  It looks like it is again rebuilding /dev/sdc1 as a spare in slot 5.  I guess I'll know more tomorrow.


-Kendall

---

### Post by darkod on 2013-04-23
No, it looks to me like slot 3. I guess the Raid Device column is more important than the Number. Those would be the raid device slots.

Also I guess it says spare until the rebuild is finished, until then it's not a fully active member with all data on it.

Lets see what happens.

PS. On another note, what you did was very bold. In theory the --create should create new array destroying the data on the old one unless you also pass the option --assume-clean, which you didn't. I'm surprised you can see the data, but lets keep the fingers crossed.

---

### Post by kendallp on 2013-04-23
> **darkod said:**
> No, it looks to me like slot 3. I guess the Raid Device column is more important than the Number. Those would be the raid device slots.

I noticed that also after posting so maybe this time it will work.


> **darkod said:**
> PS. On another note, what you did was very bold. In theory the --create should create new array destroying the data on the old one unless you also pass the option --assume-clean, which you didn't. I'm surprised you can see the data, but lets keep the fingers crossed.

I will substitute the word stupid for your bold.  I also didn't include how the first time I used --create, I did not add any options and really screwed things up. Wrong chunk size and metadata.  At that point I was sure I had ruined the data on the array because even after rebuilding with the correct options, fsck was telling me the superblock was invalid and dmesg was saying my group descriptors were corrupted.  So for anyone following this thread, please be sure you understand all of the necessary option flags to use prior to trying the --create flag.


```
#cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[5] sdf1[4] sda1[2] sdb1[1] sde1[0]
      7814047744 blocks level 5, 256k chunk, algorithm 2 [5/4] [UUU_U]
      [=======>.............]  recovery = 35.1% (687101248/1953511936) finish=909.9min speed=23195K/sec

unused devices: <none>
```


A third of the way finished.  Hopefully sda1 makes it through the resync.


-Kendall

---

### Post by rubylaser on 2013-04-23
Sorry, I'm late to the party, but without passing the --assume-clean flag to your create, I'm not sure how your data is intact (I'm glad it is, but it shouldn't be) :)  Please keep us posted.

---

### Post by kendallp on 2013-04-23
It looks like the sync failed again due to errors on sda1:

```
#cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[5](S) sdf1[4] sda1[6](F) sdb1[1] sde1[0]
      7814047744 blocks level 5, 256k chunk, algorithm 2 [5/3] [UU__U]
```

```
#sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Apr 23 13:42:48 2013
          State : clean, FAILED
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 256K

           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
         Events : 0.39

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       17        1      active sync   /dev/sdb1
       2       0        0        2      removed
       3       0        0        3      removed
       4       8       81        4      active sync   /dev/sdf1

       5       8       33        -      spare   /dev/sdc1
       6       8        1        -      faulty spare   /dev/sda1
```

```
#dmesg
[492694.191921] sd 1:0:0:0: [sda] Unhandled sense code
[492694.191923] sd 1:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[492694.191926] sd 1:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[492694.191929] Descriptor sense data with sense descriptors (in hex):
[492694.191930]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[492694.191935]         87 a9 5b 19
[492694.191938] sd 1:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[492694.191941] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 87 a9 5a 3f 00 04 00 00
[492694.191947] end_request: I/O error, dev sda, sector 2276023065
[492694.191950] raid5_end_read_request: 12 callbacks suppressed
[492694.191952] md/raid:md0: read error not correctable (sector 2276023000 on sda1).
[492694.191955] md/raid:md0: Disk failure on sda1, disabling device.
[492694.191956] md/raid:md0: Operation continuing on 3 devices.
[492694.191961] md/raid:md0: read error not correctable (sector 2276023008 on sda1).
[492694.191964] md/raid:md0: read error not correctable (sector 2276023016 on sda1).
[492694.191966] md/raid:md0: read error not correctable (sector 2276023024 on sda1).
[492694.191969] md/raid:md0: read error not correctable (sector 2276023032 on sda1).
[492694.191971] md/raid:md0: read error not correctable (sector 2276023040 on sda1).
[492694.191973] md/raid:md0: read error not correctable (sector 2276023048 on sda1).
[492694.191975] md/raid:md0: read error not correctable (sector 2276023056 on sda1).
[492694.191977] md/raid:md0: read error not correctable (sector 2276023064 on sda1).
[492694.191979] md/raid:md0: read error not correctable (sector 2276023072 on sda1).
[492694.192029] ata2: EH complete
[492694.597618] md: md0: recovery done.
[492694.618650] RAID conf printout:
[492694.618655]  --- level:5 rd:5 wd:3
[492694.618659]  disk 0, o:1, dev:sde1
[492694.618663]  disk 1, o:1, dev:sdb1
[492694.618666]  disk 2, o:0, dev:sda1
[492694.618670]  disk 3, o:1, dev:sdc1
[492694.618673]  disk 4, o:1, dev:sdf1
[492694.657479] RAID conf printout:
[492694.657483]  --- level:5 rd:5 wd:3
[492694.657487]  disk 0, o:1, dev:sde1
[492694.657489]  disk 1, o:1, dev:sdb1
[492694.657492]  disk 2, o:0, dev:sda1
[492694.657494]  disk 4, o:1, dev:sdf1
[492694.657501] RAID conf printout:
[492694.657503]  --- level:5 rd:5 wd:3
[492694.657505]  disk 0, o:1, dev:sde1
[492694.657507]  disk 1, o:1, dev:sdb1
[492694.657510]  disk 2, o:0, dev:sda1
[492694.657512]  disk 4, o:1, dev:sdf1
[492694.721290] RAID conf printout:
[492694.721295]  --- level:5 rd:5 wd:3
[492694.721300]  disk 0, o:1, dev:sde1
[492694.721303]  disk 1, o:1, dev:sdb1
[492694.721306]  disk 4, o:1, dev:sdf1
```

```
#sudo mdadm -E /dev/sd[abcef]1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Tue Apr 23 13:11:32 2013
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 62317532 - correct
         Events : 36

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     2       8        1        2      active sync   /dev/sda1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Tue Apr 23 19:45:28 2013
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 6231d1ad - correct
         Events : 41

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Tue Apr 23 19:45:28 2013
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 6231d1bf - correct
         Events : 41

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     5       8       33        5      spare   /dev/sdc1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
/dev/sde1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Tue Apr 23 19:45:28 2013
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 6231d1db - correct
         Events : 41

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8       65        0      active sync   /dev/sde1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
/dev/sdf1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Tue Apr 23 19:45:28 2013
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 6231d1f3 - correct
         Events : 41

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     4       8       81        4      active sync   /dev/sdf1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
```


Is there a way to have the mdadm sync ignore those sectors and finish the remaining data on the array?  Or would it just be best to use hdparm to write to all of those unreadable sectors?

Or, can it hurt to try and restart the array without sda1 but instead with the partially synced sdc1?  I'm going to guess it gets at least 75% through the sync.


Thanks,
-Kendall

---

### Post by rubylaser on 2013-04-24
Neither of those are great solutions.  The partially synced disk won't work, so you'll have to use /dev/sda.  I think I would buy a new disk and use gddrescue to copy all the contents onto the new disk, and then try to re-assemble the array with that.

---

### Post by kendallp on 2013-04-24
Thank you Rubylaser.  Later today I'll try gddrescue to copy sda to sdc and see if I can get the array reassembled.  Last night I started an offline test with smartctl which will not finish until later today.

---

### Post by kendallp on 2013-04-25
Ddrescue finished:

```
#sudo ddrescue -v -r3 --block-size=4KiB --force /dev/sda /dev/sdc rescue.log

About to copy 2 TBytes from /dev/sda to /dev/sdc
    Starting positions: infile = 0 B,  outfile = 0 B
    Copy block size: 16 sectors
Sector size: 4096  bytes
Max retries: 3
Direct: no    Sparse: no    Split: yes    Truncate: no

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:        2 TB,  errsize:       0 B,  current rate:    10240 B/s
   ipos:     1165 GB,   errors:       0,    average rate:   46590 kB/s
   opos:     1165 GB,     time from last successful read:       0 s
Finished
```

```
#sudo mdadm -E /dev/sd[abcef]1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Tue Apr 23 13:11:32 2013
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 62317532 - correct
         Events : 36

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     2       8        1        2      active sync   /dev/sda1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Wed Apr 24 14:42:05 2013
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 6232dc16 - correct
         Events : 43

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
mdadm: No md superblock detected on /dev/sdc1.
/dev/sde1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Wed Apr 24 14:42:05 2013
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 6232dc44 - correct
         Events : 43

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8       65        0      active sync   /dev/sde1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
/dev/sdf1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Wed Apr 24 14:42:05 2013
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 6232dc5c - correct
         Events : 43

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     4       8       81        4      active sync   /dev/sdf1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       33        5      spare   /dev/sdc1
```

```
#sudo fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa2a226e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa2a226e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63  3907024064  1953512001   fd  Linux raid autodetect
Partition 1 does not start on physical sector boundary.

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e80a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048      499711      248832   83  Linux
/dev/sdd2          501758   488396799   243947521    5  Extended
/dev/sdd5          501760   488396799   243947520   8e  Linux LVM

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc744f265

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  3907024064  1953512001   fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              64  3907029167  1953514552   fd  Linux raid autodetect

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x086bff60

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/mapper/NAS-root: 245.6 GB, 245647802368 bytes
255 heads, 63 sectors/track, 29864 cylinders, total 479780864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/NAS-root doesn't contain a valid partition table

Disk /dev/mapper/NAS-swap_1: 4148 MB, 4148166656 bytes
255 heads, 63 sectors/track, 504 cylinders, total 8101888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/NAS-swap_1 doesn't contain a valid partition table
```


Something I forgot to research before using ddrescue.  sdc is an advanced format drive so the start sector should be 2048 (or something else divisible by 8) not 63.  Does anyone know if what I have done will work or do I need to find a non-AF drive and run ddresuce again?


Thanks,
-Kendall

---

### Post by rubylaser on 2013-04-25
That's a good question about ddrescue.  It created an exact duplicate of your other drive at the block level, so I'm not sure the best way around this.  The main problem that this could create is less than ideal performance.  At this point, I'd be more concerned about recovering my data, and deal with grabbing a new disk and properly partitioning it down the line.

It looks like you just need to pass the [--block-size option]("http://www.buildingcube.com/2013/01/20/dd_rescue-gddrescues-ddrescue-for-disks-with-advanced-format-af-4kib-sectors-4096-byte/"). But, this would require do the rescue again :(  I'd still try to get it working first.

---

### Post by kendallp on 2013-04-26
I found another 2TB drive lying around so I went ahead and ran ddresuce again:

```
#sudo ddrescue -v -r3 --block-size=4KiB --force /dev/sda /dev/sdc rescue1.log

About to copy 2 TBytes from /dev/sda to /dev/sdc
    Starting positions: infile = 0 B,  outfile = 0 B
    Copy block size: 16 sectors
Sector size: 4096  bytes
Max retries: 3
Direct: no    Sparse: no    Split: yes    Truncate: no

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:        2 TB,  errsize:    4096 B,  current rate:        0 B/s
   ipos:     1165 GB,   errors:       1,    average rate:   42366 kB/s
   opos:     1165 GB,     time from last successful read:      45 s
Finished
```

```
#sudo fdisk -l

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa2a226e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x086bff60

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa2a226e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc744f265

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  3907024064  1953512001   fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              64  3907029167  1953514552   fd  Linux raid autodetect

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e80a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048      499711      248832   83  Linux
/dev/sdd2          501758   488396799   243947521    5  Extended
/dev/sdd5          501760   488396799   243947520   8e  Linux LVM

Disk /dev/mapper/NAS-root: 245.6 GB, 245647802368 bytes
255 heads, 63 sectors/track, 29864 cylinders, total 479780864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/NAS-root doesn't contain a valid partition table

Disk /dev/mapper/NAS-swap_1: 4148 MB, 4148166656 bytes
255 heads, 63 sectors/track, 504 cylinders, total 8101888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/NAS-swap_1 doesn't contain a valid partition table
```


Then removed the failing sda and rebuilt the array with the newly ddrescued drive:

```
#sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Apr 24 14:42:05 2013
          State : clean, degraded
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 256K

           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
         Events : 0.43

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       17        1      active sync   /dev/sdb1
       2       8        1        2      active sync   /dev/sda1
       3       0        0        3      removed
       4       8       81        4      active sync   /dev/sdf1
```


Checked the filesystem again and no errors.  So I added sdc1 to the array (had it not been so late I would of mounted the array first and checked the data but I should be asleep):

```
#sudo mdadm --add /dev/md0 /dev/sdc1
mdadm: added /dev/sdc1
```

```
#cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[5] sde1[0] sdf1[4] sda1[2] sdb1[1]
      7814047744 blocks level 5, 256k chunk, algorithm 2 [5/4] [UUU_U]
      [>....................]  recovery =  0.0% (879092/1953511936) finish=407.2min speed=79917K/sec
```


Looks like I will know more tomorrow.


-Kendall

---

### Post by rubylaser on 2013-04-26
That looks good so far :)

---

### Post by darkod on 2013-04-26
It looks good but it doesn't mean your data is back. Unless I missed something, after you did the --create without passing --assume-clean you never had a chance to mount the array and check the data because the rebuild was failing. Now you copied /dev/sda to another disk and are doing the rebuild, but even if it finishes without issues that doesn't mean the data is there after the --create.

If you look at the --examine output in post #36, before you tried the first ddrescue, the event counters are very low and they were much higher earlier. Not sure if that means anything. In my logic, this is the new array you created without passing --assume-clean, but it never even started working since it couldn't build itself properly. Hence the low event counters. That is my logic anyway but I might be wrong. :)

After the ddrescue you are building that array now, but what about the data??? Anyway, fingers crossed...

---

### Post by rubylaser on 2013-04-26
> **darkod said:**
> It looks good but it doesn't mean your data is back. Unless I missed something, after you did the --create without passing --assume-clean you never had a chance to mount the array and check the data because the rebuild was failing. Now you copied /dev/sda to another disk and are doing the rebuild, but even if it finishes without issues that doesn't mean the data is there after the --create.

If you look at the --examine output in post #36, before you tried the first ddrescue, the event counters are very low and they were much higher earlier. Not sure if that means anything. In my logic, this is the new array you created without passing --assume-clean, but it never even started working since it couldn't build itself properly. Hence the low event counters. That is my logic anyway but I might be wrong. :)

After the ddrescue you are building that array now, but what about the data??? Anyway, fingers crossed...

+1, you are right Darkod, I forgot about the create without the assume clean flag.  This could all be meaningless at this point (other than getting a new array setup).  Even though the fsck passed with no problem, it would still be nice to mount the array and have a look around.

---

### Post by kendallp on 2013-04-26
Array finished syncing!  

```
#cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[3] sde1[0] sdf1[4] sda1[2] sdb1[1]
      7814047744 blocks level 5, 256k chunk, algorithm 2 [5/5] [UUUUU]

unused devices: <none>
```

```
#sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Apr 26 07:18:28 2013
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 256K

           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
         Events : 0.66

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       17        1      active sync   /dev/sdb1
       2       8        1        2      active sync   /dev/sda1
       3       8       33        3      active sync   /dev/sdc1
       4       8       81        4      active sync   /dev/sdf1
```

```
sudo mdadm -E /dev/sd[abcef]1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Fri Apr 26 07:37:55 2013
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 62351baf - correct
         Events : 66

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     2       8        1        2      active sync   /dev/sda1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       8       33        3      active sync   /dev/sdc1
   4     4       8       81        4      active sync   /dev/sdf1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Fri Apr 26 07:37:55 2013
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 62351bbd - correct
         Events : 66

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       8       33        3      active sync   /dev/sdc1
   4     4       8       81        4      active sync   /dev/sdf1
/dev/sdc1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Fri Apr 26 07:37:55 2013
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 62351bd1 - correct
         Events : 66

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     3       8       33        3      active sync   /dev/sdc1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       8       33        3      active sync   /dev/sdc1
   4     4       8       81        4      active sync   /dev/sdf1
/dev/sde1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Fri Apr 26 07:37:55 2013
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 62351beb - correct
         Events : 66

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8       65        0      active sync   /dev/sde1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       8       33        3      active sync   /dev/sdc1
   4     4       8       81        4      active sync   /dev/sdf1
/dev/sdf1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 96748b59:73d20522:cced5de7:ca715931 (local to host NAS)
  Creation Time : Mon Apr 22 21:20:29 2013
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Fri Apr 26 07:37:55 2013
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 62351c03 - correct
         Events : 66

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     4       8       81        4      active sync   /dev/sdf1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       8       33        3      active sync   /dev/sdc1
   4     4       8       81        4      active sync   /dev/sdf1
```


Array mounted and my data is there.  I am sure there will be some corruption but looks like I am back up and running.  Last step should be updating mdadm.conf to the new array UUID:

```
cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 UUID=96748b59:73d20522:cced5de7:ca715931

# This file was auto-generated on Thu, 20 Dec 2012 20:33:25 -0500
# by mkconf $Id$
```


Darko, I wonder if mdadm defaults to --assume-clean if it finds an existing array on the devices specified.  In my searches during the last week, I have read other people's posts who have neglected to use --assume-clean and their data was not overwritten.  

For anyone finding this thread during their own issues, I might of gotten lucky not to lose data.  When using --create to try and rebuild an existing array, the --assume-clean flag should have been used with --create.


Thank you again Darko and Rubylaser for listening and your guidance,
-Kendall

---

### Post by rubylaser on 2013-04-26
I'm very glad that it worked out well for you.  Thanks for the final update.

---

### Post by DudeBud on 2013-12-12
Thank you kendallp, rubylaser, and darkod.  - You have saved my array, and many hours of intarwebs readings.

---

