---
title: "Expanding the drives of a RAID-5 array?"
date: 2012-07-29
forum: Server Platforms
---

### Post by schworak on 2012-07-29
Today I had to repair a drive on my RAID-5 array after the system locked up and I had to hard power off.

One of the drives was hosed but I removed it, checked it and re-added it and all is well again. 

But that got me to thinking... If I want to switch from my 1TB drives x 3 up to 2TB or even 3TB drives, how do I do that without buying all new drives, creating a new RAID and copying all the data?

Is it possible to remove one of the 1TB drives, put in a new 2TB drive in its place, let the system work its magic then repeat the process with the next drive and next drive and so on as needed?

I know it is easy to add another drive to go from say 3 drives to 4 but how do I replace a drive with a bigger drive?

---

### Post by rubylaser on 2012-07-30
> **schworak said:**
> Today I had to repair a drive on my RAID-5 array after the system locked up and I had to hard power off.

One of the drives was hosed but I removed it, checked it and re-added it and all is well again. 

But that got me to thinking... If I want to switch from my 1TB drives x 3 up to 2TB or even 3TB drives, how do I do that without buying all new drives, creating a new RAID and copying all the data?

Is it possible to remove one of the 1TB drives, put in a new 2TB drive in its place, let the system work its magic then repeat the process with the next drive and next drive and so on as needed?

I know it is easy to add another drive to go from say 3 drives to 4 but how do I replace a drive with a bigger drive?

Yes, you can add larger hard drives one at a time as you've asked very easily.  If you wanted to replace /dev/sdb1, the steps would look like this.  Although, doing a backup before a lengthy re-sync is definitely a good idea.

```
mdadm --manage /dev/md0 --fail /dev/sdb1
mdadm --manage /dev/md0 --remove /dev/sdb1
```

Replace the disk the disk with a bigger one, and setup your partition on the new drive. Then, add it to the array.
```
mdadm --manage /dev/md0 --add /dev/sdb1
```

Once, you've replaced all of the 1TB disks with 2/3/4TB disks, you can easily grow the filesystem to use the new space (in this example, my array is mounted on /storage.
```
umount /storage
fsck.ext4 /dev/md0
resize2fs /dev/md0

```
This will automatically grow the ext4 filesystem to the new size of the device. You can now remount the drive and start filling it up again!

---

### Post by CharlesA on 2012-07-30
> **rubylaser said:**
> 
Once, you've replaced all of the 1TB disks with 2/3/4TB disks, you can easily grow the filesystem to use the new space (in this example, my array is mounted on /storage.
```
umount /storage
fsck.ext4 /dev/md0
resize2fs /dev/md0

```
This will automatically grow the ext4 filesystem to the new size of the device. You can now remount the drive and start filling it up again!

Is this mdadm specific, or will it work with a hardware array? I always thought I would need to manually resize my file system if I add a new drive to my array.

---

### Post by rubylaser on 2012-07-30
> **CharlesA said:**
> Is this mdadm specific, or will it work with a hardware array? I always thought I would need to manually resize my file system if I add a new drive to my array.

Depending in your controller, you should be able replace with larger disks and expand your volume's size.  Once this is done, growing the the filesystem is the same as above (resize2fs on an unmounted array).  This is obviously, RAID card feature dependent.

---

### Post by darkod on 2012-07-30
But wasn't (isn't) raid limited to the smallest disk/partition? From that point of view, will mdadm accept the new sdb1 partition with a size larger than 1TB?

Because if you have to make it 1TB so that the array accepts it, wouldn't that be the limit for expanding the FS later?

---

### Post by CharlesA on 2012-07-30
> **rubylaser said:**
> Depending in your controller, you should be able replace with larger disks and expand your volume's size.  Once this is done, growing the the filesystem is the same as above (resize2fs on an unmounted array).  This is obviously, RAID card feature dependent.
Thanks. I believe the card I am using can do online expansion (or whatever it is called), but I'll be sure to do a full backup before messing with anything.

---

### Post by rubylaser on 2012-07-30
> **darkod said:**
> But wasn't (isn't) raid limited to the smallest disk/partition? From that point of view, will mdadm accept the new sdb1 partition with a size larger than 1TB?

Because if you have to make it 1TB so that the array accepts it, wouldn't that be the limit for expanding the FS later?

Good question :) mdadm will accept a partition the same size or larger, so you could create a 2/3/4TB partition on the new disk.  This will work fine.  mdadm will use the smallest sized partition to base the RAID5 volume size, but when all the disks have been replaced, it will use the larger partition size to base the array on.

Here's a quick example to show you. I made a (3) disk RAID5 in VBox with 1GB disks (/dev/sd[bcd]1).  Then, I'll replace each one with 2GB disks (/dev/sd[efg]1).

```
Disk /dev/sdb: 1073 MB, 1073741824 bytes
139 heads, 8 sectors/track, 1885 cylinders, total 2097152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4e8d3932

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     2097151     1047552   83  Linux

Disk /dev/sdc: 1073 MB, 1073741824 bytes
139 heads, 8 sectors/track, 1885 cylinders, total 2097152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x13854649

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048     2097151     1047552   83  Linux

Disk /dev/sdd: 1073 MB, 1073741824 bytes
139 heads, 8 sectors/track, 1885 cylinders, total 2097152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa17beaec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048     2097151     1047552   83  Linux

Disk /dev/sde: 2147 MB, 2147483648 bytes
22 heads, 16 sectors/track, 11915 cylinders, total 4194304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1f82774e

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048     4194303     2096128   83  Linux

Disk /dev/sdf: 2147 MB, 2147483648 bytes
22 heads, 16 sectors/track, 11915 cylinders, total 4194304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x517548cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            2048     4194303     2096128   83  Linux

Disk /dev/sdg: 2147 MB, 2147483648 bytes
22 heads, 16 sectors/track, 11915 cylinders, total 4194304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6fe6a9a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1            2048     4194303     2096128   83  Linux

```

Create the array
```
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sd[bcd]1
```

```
root@test:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Mon Jul 30 12:38:41 2012
     Raid Level : raid5
     Array Size : 2094080 (2045.34 MiB 2144.34 MB)
  Used Dev Size : 1047040 (1022.67 MiB 1072.17 MB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Mon Jul 30 12:39:01 2012
          State : clean, degraded, recovering 
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

 Rebuild Status : 11% complete

           Name : test:0  (local to host test)
           UUID : c678b493:e13f07fb:90a4dcf3:2fcd1191
         Events : 2

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       3       8       49        2      spare rebuilding   /dev/sdd1

```

Add a filesystem
```
mkfs.ext4 /dev/md0
```
Mount it
```
root@test:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       7.5G  1.1G  6.1G  16% /
udev            238M  4.0K  238M   1% /dev
tmpfs            99M  348K   98M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            246M     0  246M   0% /run/shm
/dev/md0        2.0G   64M  1.9G   4% /storage
```

Let's make a testfile to ensure consistency.
```
root@test:~# echo "Hello, I'm a testfile" > /storage/testfile.out
root@test:~# md5sum /storage/testfile.out 
8823d4f33a26dbdb1a05e8836b93ba43  /storage/testfile.out
```

Replace the first disk
```
mdadm --manage /dev/md0 --fail /dev/sdb1
mdadm --manage /dev/md0 --remove /dev/sdb1
```
```
mdadm --manage /dev/md0 --add /dev/sde1
```

View the detail (notice the array size is the same).
```
root@test:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Mon Jul 30 12:38:41 2012
     Raid Level : raid5
     Array Size : 2094080 (2045.34 MiB 2144.34 MB)
  Used Dev Size : 1047040 (1022.67 MiB 1072.17 MB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Mon Jul 30 12:44:54 2012
          State : clean, degraded, recovering 
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

 Rebuild Status : 6% complete

           Name : test:0
           UUID : c678b493:e13f07fb:90a4dcf3:2fcd1191
         Events : 72

    Number   Major   Minor   RaidDevice State
       4       8       65        0      spare rebuilding   /dev/sde1
       1       8       33        1      active sync   /dev/sdc1
       3       8       49        2      active sync   /dev/sdd1

```

Complete for the rest of the disks. Here's with all the disks replaced (you'll notice the size remains the same).
```
root@test:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Mon Jul 30 12:38:41 2012
     Raid Level : raid5
     Array Size : 2094080 (2045.34 MiB 2144.34 MB)
  Used Dev Size : 1047040 (1022.67 MiB 1072.17 MB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Mon Jul 30 13:01:27 2012
          State : clean 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : test:0
           UUID : c678b493:e13f07fb:90a4dcf3:2fcd1191
         Events : 137

    Number   Major   Minor   RaidDevice State
       4       8       65        0      active sync   /dev/sde1
       5       8       81        1      active sync   /dev/sdf1
       3       8       97        2      active sync   /dev/sdg1

```

Now, set the size of the array to the max available space.
```
mdadm --grow /dev/md0 --size=max
```
```
root@test:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Mon Jul 30 12:38:41 2012
     Raid Level : raid5
     **Array Size : 4190208 (4.00 GiB 4.29 GB)**
  Used Dev Size : 2095104 (2046.34 MiB 2145.39 MB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Mon Jul 30 13:02:56 2012
          State : clean, resyncing 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

  Resync Status : 56% complete

           Name : test:0
           UUID : c678b493:e13f07fb:90a4dcf3:2fcd1191
         Events : 139

    Number   Major   Minor   RaidDevice State
       4       8       65        0      active sync   /dev/sde1
       5       8       81        1      active sync   /dev/sdf1
       3       8       97        2      active sync   /dev/sdg1

```

Unmount the array, and resize the filesystem.
```
umount /storage
fsck.ext4 -f /dev/md0
resize2fs /dev/md0
```



And check that size now.
```
root@test:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       7.5G  1.1G  6.1G  16% /
udev            238M  4.0K  238M   1% /dev
tmpfs            99M  348K   98M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            246M     0  246M   0% /run/shm
**/dev/md0        4.0G   94M  3.9G   3% /storage**
```

And, let's check the consistency of our original file.
```
root@test:~# cat /storage/testfile.out 
Hello, I'm a testfile
root@test:~# md5sum /storage/testfile.out 
8823d4f33a26dbdb1a05e8836b93ba43  /storage/testfile.out

```


Also to the OP,  if you don't have backups prior to doing this, I wouldn't recommend this method for expansion (it's rather risky).

---

### Post by rubylaser on 2012-07-30
> **CharlesA said:**
> I'll be sure to do a full backup before messing with anything.
+1, this is the best idea of this whole process :) Good Luck!

---

### Post by darkod on 2012-07-30
Thanks a lot for the detailed explanation and example. That post goes to bookmarks directly. :)

---

### Post by rubylaser on 2012-07-30
> **darkod said:**
> Thanks a lot for the detailed explanation and example. That post goes to bookmarks directly. :)

No problem :)  Sometimes an example makes things a lot easier to understand (and use) for people.

---

