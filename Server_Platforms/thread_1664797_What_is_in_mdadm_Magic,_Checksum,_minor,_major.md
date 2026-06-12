---
title: "What is in mdadm: Magic, Checksum, minor, major?"
date: 2011-01-11
forum: Server Platforms
---

### Post by Kljuka on 2011-01-11
I have some problems with assembling previously working mdadm Raid5 array: 1 disk had smart problems, so I removed it and replaced with a new one. In the process of adding new drive, the second hard drive fell out of array leaving the array only with 2 drives. Now I need to decide to do either:
```

mdadm --assemble /dev/md3 --force /dev/sda3 /dev/sdb3 /dev/sdc3
or:
mdadm --create /dev/md3 --assume-clean --level=5 --verbose --raid-devices=4 /dev/sda3 /dev/sdb3 /dev/sdc3 missing
```I found out I actually don't understand what the output of commands means:
```
mdadm --detail /dev/md3
mdadm --examine /dev/sda3

**sudo mdadm --detail /dev/md3**
/dev/md3:
        Version : 00.90.03
  Creation Time : Sun Aug  3 22:51:17 2008
     Raid Level : raid5
     Array Size : 2924038464 (2788.58 GiB 2994.22 GB)
  Used Dev Size : 974679488 (929.53 GiB 998.07 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 3
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Sun Jan  9 22:25:26 2011
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 07c757a1:878150a5:3ad05579:e7ae1741
         Events : 0.213534

    Number   Major   Minor   RaidDevice State
       0       8       35        0      active sync   /dev/sdc3
       1       8       51        1      active sync   /dev/sdd3
       2       8        3        2      active sync   /dev/sda3
       3       8       19        3      active sync   /dev/sdb3
```What is:
-minor
-major
-magic (nubmer)
-UUID (is it raid based or disk based)
-events

And which numbers should be the same to forcefully rebuild array (or recreate) with less likelyhood of destroying the array?

If you have any tutorials/links covering these topics, I would really appreciate it. It seems to me that there are many tutorials covering how to assemble raid arrays but leaving out how mdadm actually works.

Thanks for all the help.

---

### Post by Doward on 2011-01-14
Since you examined the raid array (/dev/mdX) the UUID listed is the RAID array's UUID.

If you do an 'mdadm --examine /dev/sdX' where X is the number of the drive you want to check, you'll see the RAID UUID and the physical drive UUID.

I do not know what magic / minor / major numbers are.  I, too, would *love* to know what the heck those numbers mean.

Events is, I believe, a number used to keep track of how 'in sync' the discs are.  if you had one with an event number lower than the others, that disc may not be 'in sync' with the others.

---

### Post by chrislynch8 on 2011-01-14
The major version number selects which superblock format is to be used.The minor number might be used to tune handling of the format, such as suggesting where on each device to look for the superblock.

See this [http://www.mjmwired.net/kernel/Documentation/md.txt#256]("http://www.mjmwired.net/kernel/Documentation/md.txt#256") about line 111.

Rgds
Chris

---

### Post by psusi on 2011-01-14
> **chrislynch8 said:**
> The major version number selects which superblock format is to be used.The minor number might be used to tune handling of the format, such as suggesting where on each device to look for the superblock.

See this [http://www.mjmwired.net/kernel/Documentation/md.txt#256]("http://www.mjmwired.net/kernel/Documentation/md.txt#256") about line 111.

Rgds
Chris

No, it has nothing to do with superblock format.

Unix kernels identify block devices with two numbers, the major and the minor.  Major 8 is for scsi disks, and the minor number indicates which disk and partition.  Ignore them and just look at the device name instead.

Also that output says the array is up and running just fine, so you don't need to do anything to recover.

---

### Post by chrislynch8 on 2011-01-14
> **psusi said:**
> No, it has nothing to do with superblock format.

Unix kernels identify block devices with two numbers, the major and the minor.  Major 8 is for scsi disks, and the minor number indicates which disk and partition.  Ignore them and just look at the device name instead.

Also that output says the array is up and running just fine, so you don't need to do anything to recover.

So is that document about md devices useless :-? becuase I've used it for references before

---

### Post by psusi on 2011-01-14
> **chrislynch8 said:**
> So is that document about md devices useless :-? becuase I've used it for references before

No.  Why would you say that?

---

### Post by chrislynch8 on 2011-01-14
Thats where I got the minor and major numbers as being related to superblocks

---

### Post by psusi on 2011-01-14
> **chrislynch8 said:**
> Thats where I got the minor and major numbers as being related to superblocks

I don't see it claiming that anywhere.

---

### Post by psusi on 2011-01-14
> **chrislynch8 said:**
> Thats where I got the minor and major numbers as being related to superblocks

I don't see it claiming that anywhere.

---

### Post by Kljuka on 2011-01-23
I've sucessfully restored the data. Some of my findings (which might not be completelly accurate but they worked for me):

1. I figured out that minor numbers of hard disks don't change even if you change the order of disks (switch sata cables which means that /dev/sda, /dev/sdb, etc get mapped differently). This is useful to know when re-creating raid array (because you need to type the disks in correct order).

2. If you loose 2 drives (out of 4 in raid5), your raid array will go into degraded mode. This means that nothing will be written on it. Check why your disks droped out of raid (use dmseg command, smartctl). Then, if at least 3 disks seem to be OK (out of 4 in raid5 array) I recreated the array (it sounded scarry, but it actually found that the disks were a part of raid array and asked me to re-create it, so I did't loose data) with this command:
```
mdadm --create /dev/md3 --assume-clean --level=5 --verbose --raid-devices=4 /dev/sda3 /dev/sdb3 /dev/sdc3 missing
```
3. On every update within raid, events number increases. If the event number is the same on all hard drives in array, you can peacefully recreate the array (but again, type the disks in correct order - as they were adda at the time of RAID creation).
I even re-created a raid array that had disks with different events number (and up till now didn't find any problems with corupt data). I was just sure that I didn't write anything on degraded partitions and mounted them as read only partitions. And I wanted to run fsck after re-creation of the array.

4. Finally I think I've lost quite a lot of time learning how raid and mdadm works (it's quite robust). I'll be adding additional disk and switching to raid 6 to be a bit more safe and backup everything regularly using rsync.

Thanks for your help guys

---

### Post by psusi on 2011-01-23
> **Kljuka said:**
> 
1. I figured out that minor numbers of hard disks don't change even if you change the order of disks (switch sata cables which means that /dev/sda, /dev/sdb, etc get mapped differently). This is useful to know when re-creating raid array (because you need to type the disks in correct order).

No, the minor number is THE difference between sda and sdb.  The minor number of sda is 0, sdb is 16, sdc is 32, and so on.  You don't need to get them in the right order unless you are not using persistent metadata.  If the disks have raid superblocks, they identify which disk goes where in the array.

> **Kljuka said:**
> 2. If you loose 2 drives (out of 4 in raid5), your raid array will go into degraded mode. This means that nothing will be written on it.

No, if you loose one drive it becomes degraded, which means that it no longer has redundancy and can not recover from another failure.  After loosing a second disk, it is broken and completely unusable.  There is no state where it is read only.

---

### Post by doogy2004 on 2011-01-23
> **Kljuka said:**
> I have some problems with assembling previously working mdadm Raid5 array: 1 disk had smart problems, so I removed it and replaced with a new one. In the process of adding new drive, the second hard drive fell out of array leaving the array only with 2 drives.:

RAID5 can only protect your data in the event of a single disk failure. When you loose 2 disks in a RAID5 you will lose data.  To protect against a 2 disk failure you must go with RAID6. [http://en.wikipedia.org/wiki/Standard_RAID_levels](http://en.wikipedia.org/wiki/Standard_RAID_levels)

---

