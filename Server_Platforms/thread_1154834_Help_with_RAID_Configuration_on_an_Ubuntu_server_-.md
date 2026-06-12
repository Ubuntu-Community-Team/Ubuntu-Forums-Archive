---
title: "Help with RAID Configuration on an Ubuntu server -- Weird Stuff"
date: 2009-05-10
forum: Server Platforms
---

### Post by lestat on 2009-05-10
So ealier I had configured two SATA hard drives as two member of a raid level 1 array which was working fine. The OS was installed on a third disk. Unfortunately the OS hard drive died and I had to replace and reinstall the OS. I am using ubuntu server edition 8.04.
Running fdisk -l, I obtain

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xba5e9639

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ec710

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect


This means that my two hard drives are connected and still formatted as raid members. But if i try to recreate the array, using

root@reed-vault:~# mdadm --assemble /dev/md0 /dev/sdc1 /dev/sdb1
mdadm: cannot open device /dev/sdb1: No such file or directory
mdadm: /dev/sdb1 has no superblock - assembly aborted

The directory /dev/ does not contain sdb1. I have no idea why sdb1 does not have a superblock either cause sdc1 seems to have it. 

root@reed-vault:~# mdadm --assemble /dev/md0 /dev/sdc1 
mdadm: /dev/md0 assembled from 1 drive - need all 2 to start it (use --run to insist).
root@reed-vault:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdc1[1](S)
      976759936 blocks

Any ideas guys on what I am doing wrong here and why would sdb1 not show up in my /dev directory. I think that is the root of the problem.

Thanks

Lestat

---

### Post by fjgaude on 2009-05-10
Likely the issue is the array UUID in the **/etc/mdadm/mdadm.conf** is wrong. If you compare what that file has to running something like:

```
sudo mdadm -E /dev/sdb1
```

with the UUID in mdadm.conf they are not the same.

Run this to fix:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

Then reboot... everything should be back to normal.

---

### Post by lestat on 2009-05-10
I tried that but again, the problem seems to be /dev/sdb1 is not in my /dev directory.

root@reed-vault:~# mdadm -E /dev/sdb1
mdadm: cannot open /dev/sdb1: No such file or directory

However since /dev/sdb exists, i tried running it on /dev/sdb.


root@reed-vault:~# mdadm -E /dev/sdb
/dev/sdb:
          Magic : a92b4efc
        Version : 1.0
    Feature Map : 0x1
     Array UUID : 52489622:cd7265c8:fc898a24:0ef20a57
           Name : 0
  Creation Time : Tue Jul 29 18:23:14 2008
     Raid Level : raid1
   Raid Devices : 2

  Used Dev Size : 1953524896 (931.51 GiB 1000.20 GB)
     Array Size : 1953519728 (931.51 GiB 1000.20 GB)
      Used Size : 1953519728 (931.51 GiB 1000.20 GB)
   Super Offset : 1953525152 sectors
          State : clean
    Device UUID : cb06ff37:cf7d9052:7215b1dd:b69f448b

Internal Bitmap : -234 sectors from superblock
    Update Time : Fri Aug  8 20:04:21 2008
       Checksum : f1bc6bc0 - correct
         Events : 252


    Array Slot : 2 (0, failed, 1)
   Array State : uU 1 failed


Now this is weird cause it seems the superblock is on /dev/sdb. Running it on /dev/sdc1 gives me


root@reed-vault:~# mdadm -E /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 93dd2510:e37c803d:9a7ff956:34540d28 (local to host reed-vault)
  Creation Time : Mon Sep  1 21:49:56 2008
     Raid Level : raid1
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Wed Apr 29 10:17:40 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : bc462587 - correct
         Events : 0.32


      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync


MY mdadm.conf file is 

# mdadm.conf
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
#ARRAY /dev/md/0 level=raid1 metadata=1.0 num-devices=2 UUID=52489622:cd7265c8:fc898a24:0ef20a57 name=0
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=93dd2510:e37c803d:9a7ff956:34540d28 devices=/dev/sda1,/dev/sdb1


Thanks for any help

---

### Post by fjgaude on 2009-05-11
I see too many different UUIDs in the data you show, and /sdb versus /sdb1, strange!

Here's what I suggest at this point: re-name or delete your **mdadm.conf** file, remove **mdadm** from your system using **apt-get**, re-boot. Then re-install mdadm and run this command:

```
sudo mdadm --assemble --scan
```

That will give you a new mdadm.conf file auto created. You have to do this is the order suggested, and do not use any drive names in the command.

You have things all messed up using drives that have been used in arrays before, just a guess on my part. <smile>

---

