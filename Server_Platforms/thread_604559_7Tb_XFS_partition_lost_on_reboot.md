---
title: "7Tb XFS partition lost on reboot"
date: 2007-11-06
forum: Server Platforms
---

### Post by fab4am on 2007-11-06
Hi !
(I'm on ubuntu 7.10 just newly installed.)
I have array of 12 750gb disks in hardware Raid 6 that gives me a 7Tb partition. I tried to format it in ext3, but it took too much time, so I tried in Reiserfs, but the partition were lost on reboot, and now i'm trying XFS.

So I created the partition with parted, because fdisk can't do more that 2tb partitions.
It's ok, I can do what I want but...

on reboot, there is a Superblock problem, something like that. When I check with xfs_check :

xfs_check: unexpected XFS SB magic number 0x00000000
xfs_check: read failed: Invalid argument
xfs_check: data size check failed
cache_node_purge: refcount was 1, not zero (node=0x681420)
xfs_check: cannot read root inode (22)
bad superblock magic number 0, giving up

So, I tried to delete the partition with parted, to recreate a new one. No problem. But when I mount the new partition, all the data that were on my deleted partition are there !!! That's of course not a problem, but I'm wondering if there's a way to have this partition work directly without having to delete and recreate it ?

I checked the /proc/partition before and after doing parted :

BEFORE
major minor  #blocks  name
 104     0   35532720 cciss/c0d0
 104     1   34025638 cciss/c0d0p1
 104     2          1 cciss/c0d0p2
 104     5    1502046 cciss/c0d0p5
 105     0 7325417080 cciss/c1d0
 105     1  **882966102** cciss/c1d0p1

AFTER
major minor  #blocks  name
 104     0   35532720 cciss/c0d0
 104     1   34025638 cciss/c0d0p1
 104     2          1 cciss/c0d0p2
 104     5    1502046 cciss/c0d0p5
 105     0 7325417080 cciss/c1d0
 105     1 **7325417046** cciss/c1d0p1


So, any idea what I could do ? 

Thanks a lot
Amandine

---

### Post by pkese on 2007-11-06
Same problem here. I have a 3.6 TB XFS partition that I can't mount upon reboot. 

I have set the partition table using parted as suggested in the >2TB Howto.

What I get upon mount is
```
mount: /dev/sdb1: can't read superblock
```

and /var/log/messages say

```
Nov  6 16:29:32 carbon kernel: [71530.416999] attempt to access beyond end of device
Nov  6 16:29:32 carbon kernel: [71530.417005] sdb1: rw=0, want=7324216064, limit=3029248957
Nov  6 16:29:32 carbon kernel: [71530.417016] XFS: size check 2 failed
```

Parted says 
```
peter@carbon:~$ sudo parted /dev/sdb print

Disk /dev/sdb: 3750GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      17.4kB  3750GB  3750GB  xfs          primary       

```

But /proc/partitions on the other hand says 
```
peter@carbon:~$ cat /proc/partitions 
major minor  #blocks  name

   8     0  244140544 sda
   8     1  234267831 sda1
   8     2          1 sda2
   8     5    9871911 sda5
   8    16 3662108160 sdb
   8    17 1514624478 sdb1

```

It seems something is wrong with >2TB partition tables, but I don't yet know how to approach that problem.

Any ideas anyone?!

Best regards,
Peter

---

### Post by pkese on 2007-11-06
Yes, it is the same here. If i recreate the partition using parted, I can simply remount the partition and all the data is stil there.

Also suddenly /proc/partitions reports correct information:
peter@carbon:~$ cat /proc/partitions 
```
major minor  #blocks  name

   8     0  244140544 sda
   8     1  234267831 sda1
   8     2          1 sda2
   8     5    9871911 sda5
   8    16 3662108160 sdb
   8    17 3662108126 sdb1
```

So it is reboot that messes things up.

---

### Post by pkese on 2007-11-08
Ok, it seems to be the Ubuntu parted problem that can be fixed by rebuilding the parted from default GNU sources. 

Here are some references [http://ubuntuforums.org/showthread.php?t=429986&highlight=2tb+partition]("http://ubuntuforums.org/showthread.php?t=429986&highlight=2tb+partition")

and [https://bugs.launchpad.net/ubuntu/+source/parted/+bug/107326]("https://bugs.launchpad.net/ubuntu/+source/parted/+bug/107326")

---

### Post by pkese on 2007-11-08
Ok, so I rebuilt parted from sources, ran it and it says

```
peter@carbon:~/parted-1.8.8/parted$ sudo ./parted /dev/sdb print
Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? Yes
Model: Areca ARC-1160-VOL#01 (scsi)
Disk /dev/sdb: 3750GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      17.4kB  3750GB  3750GB  xfs          primary
```

Then I did 'mklabel gpt', etc, and upon reboot, the filesystem mounted without any problems, partitions were correct, etc...

It seems to be an Ubuntu parted bug.

---

### Post by fab4am on 2007-11-08
What a good news !!!
Thanks a lot for your replies. I did the same as You, and now it works too, without loosing m data, I just deleted and recreated the partition with the new parted :)

Thanks ! :)

Amandine

---

