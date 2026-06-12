---
title: "Linux software raid, mdadm and strange errors.."
date: 2012-08-07
forum: Server Platforms
---

### Post by w1z4rd on 2012-08-07
So this is the story.

Client brings in ubuntu linux server with 5 hard disks. 4 of the disks are in linux software raid and 1 of the disks holds the operating system. I am unable to boot up the server and need a rescue cd to see anything.

Using the following command I am able to recreate the raid array:

```
mdadm --create /dev/md0 -n 4 -c 256 -l 5 -p left-symmetric --assume-clean /dev/sda1 /dev/sdc1 /dev/sdd1 /dev/sde1
```

Normally at this stage I could just mount the raid array with the command: 
```
mount /dev/md0 /mntpoint
```

However, when I try to this I get the following error:

```
The device '/dev/md0' doesn't seem to have a valid NTFS. Maybe the wrong device is used? Or the whole disk instead of a partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

None of the drives are NTFS drives, they all show as LINUX RAID when I fdisk -l.

Any suggestions? :(

---

### Post by rubylaser on 2012-08-07
Did you try to assemble the array before you jumped right to re-creating the superblock metadata on each disk?  Do you have the metadata info from any of the disks prior to re-creating the array? (mdadm -E /dev/sdb1, etc) Here are just a bunch of questions:

1. When you re-create the array, you need to ensure that the disk order, chunk size, and metadata version are all exactly the same or your array will not work.   Are you certain that all of these values are correct?
2. Did you smart test all of the disks to verify that all of them are healthy?
3. Have you tried to run the mount command at specify the filesystem rather than having mount choose the filesystem type for you?

---

### Post by w1z4rd on 2012-08-07
> **rubylaser said:**
> Did you try to assemble the array before you jumped right to re-creating the superblock metadata on each disk?  Do you have the metadata info from any of the disks prior to re-creating the array? (mdadm -E /dev/sdb1, etc) Here are just a bunch of questions:

No. I used the create command as per a wiki suggestions. I was actually following these instructions: [http://wiki.centos.org/fr/TipsAndTricks/Repair_RAID5_Volumes](http://wiki.centos.org/fr/TipsAndTricks/Repair_RAID5_Volumes)

> 1. When you re-create the array, you need to ensure that the disk order, chunk size, and metadata version are all exactly the same or your array will not work.   Are you certain that all of these values are correct?

I did a mdadm -E of the drives and built my command out of the variables listed on the drives.

> 2. Did you smart test all of the disks to verify that all of them are healthy?

I could not pick up any errors with SMART tools

> 3. Have you tried to run the mount command at specify the filesystem rather than having mount choose the filesystem type for you?
No I have not. The raid array should be ext3. Would it be something like mount.ext3 /dev/md0 /mnt/raid ?

---

### Post by w1z4rd on 2012-08-07
Here is some additional information:

```
root@sysresccd /home/etc % fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00033916

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00056c82

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63      208844      104391   83  Linux
/dev/sdb2          208845     4401809     2096482+  82  Linux swap / Solaris
/dev/sdb3         4401810   488392064   241995127+  83  Linux

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00076244

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b5173

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000955c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63  3907024064  1953512001   fd  Linux raid autodetect
```

also

```
root@sysresccd /home/etc % mdadm --create /dev/md0 -n 4 -c 256 -l 5 -p left-symmetric --assume-clean /dev/sda1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: /dev/sda1 appears to contain an ext2fs file system
    size=1565568512K  mtime=Wed Jul 18 05:51:09 2012
mdadm: /dev/sda1 appears to be part of a raid array:
    level=raid5 devices=3 ctime=Tue Aug  7 10:58:27 2012
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid5 devices=3 ctime=Tue Aug  7 10:59:17 2012
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid5 devices=3 ctime=Tue Aug  7 10:59:17 2012
mdadm: /dev/sde1 appears to contain an ext2fs file system
    size=491826688K  mtime=Wed Jul 18 05:51:09 2012
mdadm: /dev/sde1 appears to be part of a raid array:
    level=raid5 devices=3 ctime=Tue Aug  7 10:59:17 2012
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.
root@sysresccd /home/etc %
```

and 

This is the error I get:

```
root@sysresccd /etc % mount /dev/md0 /mnt/raid
NTFS signature is missing.
Failed to mount '/dev/md0': Invalid argument
The device '/dev/md0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
root@sysresccd /etc %
```

---

### Post by rubylaser on 2012-08-07
> **w1z4rd said:**
> No. I used the create command as per a wiki suggestions. I was actually following these instructions: [http://wiki.centos.org/fr/TipsAndTricks/Repair_RAID5_Volumes](http://wiki.centos.org/fr/TipsAndTricks/Repair_RAID5_Volumes)



I did a mdadm -E of the drives and built my command out of the variables listed on the drives.



I could not pick up any errors with SMART tools


No I have not. The raid array should be ext3. Would it be something like mount.ext3 /dev/md0 /mnt/raid ?

That wiki entry is for multiple failed drives.  I would bet that one (or more) disks dropped out out your array and made it inactive.  This could have been seen in the superblock metadata by viewing the event counters on each disk.  The best thing to do first is to try to assemble the array, not overwrite all of the superblock metadata with a new create command.  Do you have a copy of the output from mdadm -E from your drives prior to re-creating the array?

Give it a try mounting like this
```
mount -t ext3 /dev/md0 /mnt/raid
```

---

