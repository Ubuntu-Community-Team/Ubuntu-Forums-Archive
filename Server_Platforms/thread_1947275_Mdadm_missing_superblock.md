---
title: "Mdadm missing superblock"
date: 2012-03-26
forum: Server Platforms
---

### Post by ghostfish on 2012-03-26
After restarting my server today, I attempted to restart my 4 disk mdadm RAID 5 array as follows.
```

$ mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: no recogniseable superblock on /dev/sdb1
mdadm: /dev/sdb1 has no superblock - assembly aborted

```Obviously, this is bad, it appears somehow when I restarted it managed to nuke the md superblock on /dev/sdb1.  fdisk -l outputs the following.
```

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00044e32

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00073923

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000681ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009b0cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      243201  1953512001   fd  Linux raid autodetect

```So it looks like /dev/sdb1 is still detecting as a RAID drive, and the problem is confined to the md superblock.  I have no reason to believe that there is any problem with the actual data on the drive, so I suspect I just need to recreate the superblock.  The other drives' superblocks still seem to be alright.
```

$ sudo mdadm --misc --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 8e57bf52:4e996d1c:0982764f:c62ddde2
  Creation Time : Mon Aug 16 01:59:16 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Mar 26 08:44:44 2012
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 66175c75 - correct
         Events : 3182

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       17        0      active sync
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
$ sudo mdadm --misc --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 8e57bf52:4e996d1c:0982764f:c62ddde2
  Creation Time : Mon Aug 16 01:59:16 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Mar 26 08:44:44 2012
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 66175c87 - correct
         Events : 3182

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       49        2      active sync   /dev/sdd1

   0     0       8       17        0      active sync
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
$ sudo mdadm --misc --examine /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 8e57bf52:4e996d1c:0982764f:c62ddde2
  Creation Time : Mon Aug 16 01:59:16 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Mar 26 08:44:44 2012
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 66175c99 - correct
         Events : 3182

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       65        3      active sync   /dev/sde1

   0     0       8       17        0      active sync
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
$ sudo mdadm --misc --examine /dev/sdb1
mdadm: No md superblock detected on /dev/sdb1.
$


```After Googling around, it seems the best way to do this is the re-create the entire array with the following command.
```

mdadm --create /dev/md0 --assume-clean --level=5 --verbose --raid-devices=4 missing /dev/sdc1 /dev/sdd1 /dev/sde1

```My questions are:
1) Is this the right way to recreate the missing superblock?
2) This "creation" is intelligent and won't overwrite any of my data on the good 3 drives, will it?
3) Is this recreation going to assemble an array with the three good drives and then repair the array onto the fourth drive and assume it's empty, or will it just add the superblock and then see that the data is already there?
4) Is "missing" the proper option in the command above or should I specify "/dev/sdb1"?  What's the difference? (I assume it has to do with the answer to question 3 above)
5) Anything else I need to know?

Obviously my #1 concern is not making things worse by accidentally deleting data while running a command trying to fix the array.  At this point no data is lost, because I only have 1 borked disk in a RAID5.  Breaking any more disks trying to fix the first would be unacceptable.  Thanks in advance for your help.

---

### Post by rubylaser on 2012-03-26
It's highly unlikely that restarting killed the superblock unless there's something wrong with the disk.  The first thing to do is verify your disk is good.
```
apt-get install smartmontools
smartctl -d ata -a /dev/sdb
```
If it's okay, then you can proceed.

There's no need to recreate the array at this point if the your array starts up fine without including the messed up /dev/sdb. Are you sure you didn't accidentally build your array with the raw device /dev/sdb instead of the partition in the first place?

Check like this.
```
mdadm -E /dev/sdb
```

If this contains a superblock, you can reassemble with that device included.

If there is no superblock on that either, you can just assemble your array and leave /dev/sdb1 out.  This will assemble it degraded.  Then you can add your /dev/sdb1 and let it resync.  Here are the steps I would follow. 
```

mdadm --zero-superblock /dev/sdb
mdadm --zero-superblock /dev/sdb1
mdadm --assemble /dev/md0 /dev/sd[cde]1
mdadm --add /dev/md0 /dev/sdb1
watch cat /proc/mdstat
```

Once, it's done syncing you should be all set.  Just as an aside, I would really consider adding an 2TB disk and moving to a RAID6.  If you have no backup, which it sounds like you don't, having only 1 disk between you and a total data loss is a pretty scary thought.

---

### Post by ghostfish on 2012-03-26
> **rubylaser said:**
> It's highly unlikely that restarting killed the superblock unless there's something wrong with the disk.
That's what I thought too, and as it turns out, it's true.  After another reboot the superblock was found just fine and I was able to start the array.  A strange error, to be sure, since the drive showed up in fdisk just fine and didn't throw any errors when trying to access it, just didn't seem to have a superblock in mdadm's eyes.  Weird.

Moral of the story - Always turn it off and back on, ideally a couple times.  Noob mistake, that.

---

### Post by rubylaser on 2012-03-26
Glad you got it working.  Please mark the thread as solved under the Thread Tools at the top of the page.

---

