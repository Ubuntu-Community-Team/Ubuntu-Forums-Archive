---
title: "Raid 1 with missing disk incorrect size"
date: 2013-07-03
forum: Server Platforms
---

### Post by harveyd on 2013-07-03
I have a single disk that is 3TB in size with a single partition:-

```
Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
90 heads, 3 sectors/track, 21705678 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000e8309


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  4294967294  2147482623+  fd  Linux RAID autodetect

```

I create a RAID1 array with mdadm with the 'missing' command as I will plan to add in the second disk later. I created the array with:-

```
mdadm --create /dev/md0 --level=1 --raid-disks=2 missing /dev/sdb1
```

However mdadm is reporting only 2.1TB:-

```
/dev/md0:
        Version : 1.2
  Creation Time : Wed Jul  3 20:45:12 2013
     Raid Level : raid1
     Array Size : 2147351360 (2047.87 GiB 2198.89 GB)
  Used Dev Size : 2147351360 (2047.87 GiB 2198.89 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent


    Update Time : Wed Jul  3 20:45:24 2013
          State : clean, degraded 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0


           Name : nas:0  (local to host nas)
           UUID : 0fb0aec2:a9687ba3:41d14294:83f2e120
         Events : 2


    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       17        1      active sync   /dev/sdb1

```

Any ideas why?

---

### Post by steeldriver on 2013-07-03
How did you create the underlying sdb1 partition? did you remember to set the partition table type as GPT?

---

### Post by harveyd on 2013-07-03
I think I have just been working that out! Just changed it to GPT and having better results

---

### Post by harveyd on 2013-07-04
> **steeldriver said:**
> How did you create the underlying sdb1 partition? did you remember to set the partition table type as GPT?

As you suggested and what I had just figured out for my self was indeed was the GPT partition table.

For others interested using fdisk to create partitions will be limited to just over 2TB as it will be using the msdos partition table. Using 'parted' and the GPT table will fix this:-

```
parted /dev/sdb

(parted) mklabel gpt

(parted) unit TB

(parted) mkpart primary 0.00TB 3.00TB

(parted) quit
```

I then needed to change the type to be raid so:-

```
fdisk /dev/sdb
```

Typed 't' for type, 'fd' for raid and 'w' to write. I wan then able to:-

```
mdadm --create /dev/md0 --level=1 --raid-disks=2 missing /dev/sdb1

```
And mdadm reported the correct 3TB size. I then set up lvm and ext4 on top of that as per normal

---

### Post by steeldriver on 2013-07-04
Glad you got it figured out - just for reference, I think it *should* have been possible to change the partition type to RAID from within parted

```
(parted) set 1 raid on
```

(where 1 is the partition number)

---

### Post by harveyd on 2013-07-04
> **steeldriver said:**
> Glad you got it figured out - just for reference, I think it *should* have been possible to change the partition type to RAID from within parted

```
(parted) set 1 raid on
```

(where 1 is the partition number)

That's really helpful, thanks! Will try that on the second disk

---

### Post by steeldriver on 2013-07-04
TBH I've forgotten most of the little I knew about RAID - it's possible that mdadm sets the flag anyway when you create the array, but it's probably good practice to do it either way

---

### Post by SaturnusDJ on 2013-07-05
Flag is not mandatory. But usefull indeed.

Read this post about partitioning:
[http://ubuntuforums.org/showthread.php?t=2110658&p=12484473#post12484473](http://ubuntuforums.org/showthread.php?t=2110658&p=12484473#post12484473)

---

