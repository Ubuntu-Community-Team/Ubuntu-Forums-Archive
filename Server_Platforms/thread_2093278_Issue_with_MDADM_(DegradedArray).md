---
title: "Issue with MDADM (DegradedArray)"
date: 2012-12-10
forum: Server Platforms
---

### Post by Platano on 2012-12-10
I'm having a problem with one of my hard drives as I have been receiving this email for the past few days.

```
"A DegradedArray event had been detected on md device /dev/md127."
```

I decided to Google further and looked into the contents of my mdstat file, this is the output:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : active (auto-read-only) raid1 sda6[0]
      3904500 blocks super 1.2 [2/1] [U_]
      
md3 : active raid1 sda8[0] sdb7[2]
      9763768 blocks super 1.2 [2/2] [UU]
      
md2 : active raid1 sda7[0] sdb6[1]
      1950708 blocks super 1.2 [2/2] [UU]
      
md1 : active raid1 sda5[0] sdb5[1]
      242676 blocks super 1.2 [2/2] [UU]
      
md0 : active raid1 sda1[0] sdb1[1]
      975860 blocks super 1.2 [2/2] [UU]
      
md6 : active raid1 sda11[0] sdb10[1]
      97653688 blocks super 1.2 [2/2] [UU]
      
md4 : active raid1 sda9[0] sdb8[1]
      9763768 blocks super 1.2 [2/2] [UU]
      
md5 : active raid1 sda10[0] sdb9[1]
      19528632 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>
```

And some more details on md127

```
root@falcon:# mdadm --detail /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Thu Aug 30 18:15:01 2012
     Raid Level : raid1
     Array Size : 3904500 (3.72 GiB 4.00 GB)
  Used Dev Size : 3904500 (3.72 GiB 4.00 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Tue Sep 18 14:44:17 2012
          State : clean, degraded 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : ubuntu:7
           UUID : 0c73441d:a58d1074:24ad16d8:128329a3
         Events : 41

    Number   Major   Minor   RaidDevice State
       0       8        6        0      active sync   /dev/sda6
       1       0        0        1      removed
```

I can see that the state of the drive is removed. I am very new to this and I have no idea how to proceed. What would be the next logical step? I'm assuming I have to rebuild my RAID array? I have run a smart test and all my drives seem to be in good health.

Could anyone point me towards the right direction? Thanks!

---

### Post by darkod on 2012-12-10
Which partition from sdb should make the array together with sda6? The mdstat shows that not all md devices are made of partitions with the same number from both disks.

You can check the partition first with something like:
sudo mdadm -E /dev/sdbX

If it looks comparable to sda6, you can add it to device md127. And usually md127 seems to be added by the system. Do you remember what number should the array have? I assume you didn't create it with 127.

What does /etc/mdadm/mdadm.conf contain?

---

### Post by Platano on 2012-12-11
Thanks for your assistance!

To tell you quite frankly, I don't know which partition from sdb makes the array with sda6. This is a friends server and it was managed by someone else before, I'm just trying to help him sort out this issue.

Is there anyway I can find out which disks or partitions make up the array?

Here's the contents of my configuration -

```

root@falcon:~# cat /etc/mdadm/mdadm.conf
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
HOMEHOST falcom

# instruct the monitoring daemon where to send mail alerts
MAILADDR my@email.com

# definitions of existing MD arrays
ARRAY /dev/md/3 metadata=1.2 UUID=43a5e7f6:ef3d07f0:aca66d8d:19cef933 name=ubuntu:3
ARRAY /dev/md/0 metadata=1.2 UUID=a8eec62a:485fe0fb:80d0d71b:55161abd name=ubuntu:0
ARRAY /dev/md/1 metadata=1.2 UUID=686ddd20:2ab0ab1c:7f7edfe4:536f1a32 name=ubuntu:1
ARRAY /dev/md/2 metadata=1.2 UUID=1f1d1074:acafc866:0376536a:cb13ce42 name=ubuntu:2
ARRAY /dev/md/4 metadata=1.2 UUID=a73f0b5c:380426cb:03c0a8eb:7128e347 name=ubuntu:4
ARRAY /dev/md/5 metadata=1.2 UUID=33042af7:f4a66fb2:a96a8376:1837747e name=ubuntu:5
ARRAY /dev/md/6 metadata=1.2 UUID=be467d34:742012c0:4803a100:a3930c6f name=ubuntu:6

# This file was auto-generated on Thu, 30 Aug 2012 18:24:03 -0500
# by mkconf $Id$

```

---

