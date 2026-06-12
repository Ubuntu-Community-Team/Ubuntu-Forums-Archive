---
title: "System locked up.  RAID will not start."
date: 2011-05-05
forum: Server Platforms
---

### Post by mn_voyageur on 2011-05-05
My system locked up while copying files last night.  

My RAID array will not start.  I did verify my UUID's.  (Lesson learned.)

I do not understand a few things.
[INDENT]1. Why do different drives show "active sync" on different drives?

2. Why does "Disk Utility" tell me the RAID is not running and when I try to assemble the RAID, mdadm returns:
    mdadm: device /dev/md0 already active - cannot assemble it[/INDENT]

When I try to start the RAID using "Disk Utility":
```
Error assembling array: mdadm exited with exit code 1: mdadm: cannot open device /dev/sdd1: Device or resource busy
mdadm: /dev/sdd1 has no superblock - assembly aborted
```

So, I examine sdd1:
```
sudo mdadm -E /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : b40cc711:46ef5048:1178d5b1:7b4fd811 (local to host 10)
  Creation Time : Mon Feb 21 05:24:20 2011
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 2
Preferred Minor : 0

    Update Time : Thu May  5 06:22:35 2011
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 64e1fb7 - correct
         Events : 2581

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       49        0      active sync   /dev/sdd1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       8       17        3      active sync   /dev/sdb1
```

This matches /sdb1:
```
sudo mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : b40cc711:46ef5048:1178d5b1:7b4fd811 (local to host 10)
  Creation Time : Mon Feb 21 05:24:20 2011
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 2
Preferred Minor : 0

    Update Time : Thu May  5 06:22:35 2011
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 64e1f9d - correct
         Events : 2581

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       17        3      active sync   /dev/sdb1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       8       17        3      active sync   /dev/sdb1
```

So, I examine /sda1:
```
sudo mdadm -E /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : b40cc711:46ef5048:1178d5b1:7b4fd811 (local to host 10)
  Creation Time : Mon Feb 21 05:24:20 2011
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Mar 17 06:47:23 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 60d832d - correct
         Events : 155

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8        1        2      active sync   /dev/sda1

   0     0       8       49        0      active sync   /dev/sdd1
[COLOR="Red"]   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8        1        2      active sync   /dev/sda1[/COLOR]
   3     3       8       17        3      active sync   /dev/sdb1
```

And finally /sdc1:
```
sudo mdadm -E /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : b40cc711:46ef5048:1178d5b1:7b4fd811 (local to host 10)
  Creation Time : Mon Feb 21 05:24:20 2011
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Mon Apr 11 05:54:13 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 62e6c83 - correct
         Events : 182

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       49        0      active sync   /dev/sdd1
[COLOR="Red"]   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed[/COLOR]
   3     3       8       17        3      active sync   /dev/sdb1
```

---

### Post by dtfinch on 2011-05-05
What does "cat /proc/mdstat" say?

---

### Post by mn_voyageur on 2011-05-05
```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd1[0] sdb1[3]
      1953519872 blocks
```

---

### Post by rubylaser on 2011-05-06
What do you have in /etc/mdadm/mdadm.conf?

---

### Post by mn_voyageur on 2011-05-06
Okay.  So, what catches your eye?  

MarkN

[HTML]# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid6 num-devices=4 UUID=b40cc711:46ef5048:1178d5b1:7b4fd811


# This file was auto-generated on Mon, 21 Feb 2011 04:49:14 -0600
# by mkconf $Id$[/HTML]

---

### Post by mn_voyageur on 2011-05-09
Bump

---

### Post by rubylaser on 2011-05-10
Your mdadm.conf file is fine.  Did something happen to cause one of the disks to drop out of the array?  Are all of the disks functioning properly, and not showing SMART errors?  The good news is that all of the disks are showing the same UUID.  I would stop the running mdadm array, and try to force the array together properly.  

```
sudo -i
mdadm --stop /dev/md0
mdadm --assemble --force /dev/md0 /dev/sd[abcd]1
```

---

### Post by mn_voyageur on 2011-05-10
Okay ...

Why does the drive letters change on the drives assigned to the array?  This machine has 5 drives.  4 - 1 TB drives and 1 - 160 GB.  The 160 is my system drive.  A friend told me to run everything from a system drive and not boot from the RAID array.  

Anyway, today the array consists of sd[bcde]

```
mdadm --assemble --force /dev/md0 /dev/sd[bcde]1
mdadm: failed to RUN_ARRAY /dev/md0: Input/output error
```

```
mdadm --stop /dev/md0
mdadm: stopped /dev/md0

```
Tried to spell everything out:
```
mdadm --assemble --force /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: failed to RUN_ARRAY /dev/md0: Input/output error
```


When I try to start the RAID from the GUI:  (Right Click > Start Multi-disk drive)
```
Failed activating drive: Error assembling array: mdadm exited with exit code 1: mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: /dev/sdc1 has no superblock - assembly aborted
```

```
 fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001283a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18708   150265856   83  Linux
/dev/sda2           18708       19458     6022145    5  Extended
/dev/sda5           18708       19458     6022144   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000baa15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004600b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00054e04

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006c96e

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001   fd  Linux raid autodetect
```

I appreciate everyone's time and assistance.

MarkN

---

### Post by rubylaser on 2011-05-11
> **mn_voyageur said:**
> Okay ...

Why does the drive letters change on the drives assigned to the array?

The drives are being presented to the OS in an inconsistent order from your SATA controller.  Based on your previous problem with drives failing out of the array, I'm guessing that you have a hardware problem causing soft disconnects (bad sata controller, or sata cables).  

The drive positions are not a big deal unless you specifically describe the drives in your mdadm.conf (you don't have this).  You could create a udev rule to have the drives show up in a consistent order, but that's not your problem here.

It looks like the superblocks are screwed up on some of your disks, and no amount of assembling is going to put the array back together.  The only way to fix this is to recreate the superblocks for the array.  I know that sounds scary, but mdadm is smart enough to not overwrite your data.  Here's an example...
[http://kevin.deldycke.com/2007/03/how-to-recover-a-raid-array-after-having-zero-ized-superblocks/]("http://kevin.deldycke.com/2007/03/how-to-recover-a-raid-array-after-having-zero-ized-superblocks/")

You need to recreate the array with the same setup as before.  Do you have the output of cat /proc/mdstat when your array was working properly?  You'd just need to do something like this (but you'll want the disks in the same order as before).

```
mdadm --create /dev/md0 -v -l 5 -n 4 /dev/sd[dcbe]1
```
**[COLOR="Red"]^ This is just an example, you'll want the disks in the same order as before.[/COLOR]**

---

### Post by mn_voyageur on 2011-05-12
Success!

Okay.  I ran this:
```
sudo mdadm --assemble --force /dev/md0 --uuid=b40cc711:46ef5048:1178d5b1:7b4fd811
mdadm: /dev/md0 has been started with 2 drives (out of 4).
```

Does running this command make sense?

Also, Rubylaser, you mentioned sata cables might be an issue.  The cables I am using came with my hdd's.  Should I consider replacing them?  If so, what would you recommend?

Finally, other than keeping back-ups of the data on my array, is there anything else that I should be backing up on a regular basis?

I appreciate all the help.

MarkN

---

### Post by rubylaser on 2011-05-13
That command makes sense, but only when mdadm isn't confused about the disks.  It's normally better to force assemble it by mentioning the disks specifically as I showed earlier.  What's the output of this?
```
cat /proc/mdstat
```

It started the array with only 2 of the 4 drives, so you've lost both parity drives on the RAID6 at this point.  I think I would backup my data, and recreate the array.  

In regards to SATA cables, probably the quickest way to check is to use SMART on the disks and look for UDMA_CRC_Error_Count numbers greater than 0.  Like this...
```
root@fileserver:~# smartctl -a -d ata /dev/sdb | grep UDMA
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       [COLOR="Red"]0[/COLOR]
```
This can indicate a bad SATA cable.  Also, what type of hard drives are you using?

I normally just buy my cables from [monoprice.com]("http://www.monoprice.com/products/search.asp?keyword=sata+cable&x=23&y=6")

---

