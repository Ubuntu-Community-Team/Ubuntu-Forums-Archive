---
title: "MDADM Raid5 produces big amounts of write actions to Array"
date: 2014-06-23
forum: Server Platforms
---

### Post by martin113 on 2014-06-23
Hello,

today I build a mdadm raid 5 on 3 Western Digital WD4000F9YZ harddisks. In general I followed the guide at [http://wiki.ubuntuusers.de/Software-RAID](http://wiki.ubuntuusers.de/Software-RAID) (unfortunately in german) Everything worked fine, and I have my new /dev/md0 running. But the problem arises that the array do a write access exactly every second right after mounting the array. So The NAS does a "Klack-Klack" sound every second.  In an earlier mdadm Raid with 4 1.5TiB Files this was not the case. 
I can stop that noise by unmounting the array and directly after remounting it starts again. So I have no clue what to do to solve this. 

Here some more info:

Ah I'm running Ubunutu Server 14.04 LTS 64bit

mdadm.conf (last two lines written by hand)
```
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

# This file was auto-generated on Mon, 23 Jun 2014 00:49:43 +0200
# by mkconf $Id$
DEVICE /dev/sd[bcd]1
ARRAY /dev/md0 level=raid5 num-devices=3 devices=/dev/sdb1,/dev/sdc1,/dev/sdd1 metadata=1.2 UUID=47911b33:cb503032:bf48a3e2:011bf833

```

fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=f9b261a4-4c63-4242-ad7a-c8abec4d2ec0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5cbb29da-a1a2-4a5a-bf5d-be91b04c2948 none            swap    sw              0       0
/dev/md0 /media/daten ext4 defaults 0 2


```

mdadm --detail /dev/md0
```

/dev/md0:
        Version : 1.2
  Creation Time : Mon Jun 23 11:18:57 2014
     Raid Level : raid5
     Array Size : 7813764096 (7451.79 GiB 8001.29 GB)
  Used Dev Size : 3906882048 (3725.89 GiB 4000.65 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Mon Jun 23 23:27:18 2014
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : ubnas:0  (local to host ubnas)
           UUID : 47911b33:cb503032:bf48a3e2:011bf833
         Events : 927

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       3       8       49        2      active sync   /dev/sdd1


```

cat /proc/mdstat
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[1] sdb1[0] sdd1[3]
      7813764096 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]

```


If you need anything else let me know.. 

There is also a Plex Media Server installed which is looking in the mounted Array at /media/daten for mediafiles (which are actually not there yet). So I thought that the activity is produced by this Plexserver. To check I mounted the array at another point (/media/test) where no indexing by Pley occurs, but HDD activity remains the same. 

Please can you help me?

Regards Martin

EDIT:

Additional infos:
After activating i/o logging with 
echo 1 > /proc/sys/vm/block_dump

[FONT=arial]I got this log:[/FONT]

tail /var/log/syslog
```

Jun 24 00:03:48 ubnas kernel: [ 1456.826696] md0_raid5(178): WRITE block 8 on sdb1 (1 sectors)
Jun 24 00:03:49 ubnas kernel: [ 1457.222435] ext4lazyinit(362): WRITE block 3779090688 on md0 (768 sectors)
Jun 24 00:03:49 ubnas kernel: [ 1457.222484] md0_raid5(178): WRITE block 8 on sdc1 (1 sectors)
Jun 24 00:03:49 ubnas kernel: [ 1457.222498] md0_raid5(178): WRITE block 8 on sdd1 (1 sectors)
Jun 24 00:03:49 ubnas kernel: [ 1457.222505] md0_raid5(178): WRITE block 8 on sdb1 (1 sectors)
Jun 24 00:03:49 ubnas kernel: [ 1457.235037] ext4lazyinit(362): WRITE block 3779091456 on md0 (1024 sectors)
Jun 24 00:03:49 ubnas kernel: [ 1457.235170] ext4lazyinit(362): WRITE block 3779092480 on md0 (256 sectors)
Jun 24 00:03:49 ubnas kernel: [ 1457.454279] md0_raid5(178): WRITE block 8 on sdc1 (1 sectors)
Jun 24 00:03:49 ubnas kernel: [ 1457.454294] md0_raid5(178): WRITE block 8 on sdd1 (1 sectors)
Jun 24 00:03:49 ubnas kernel: [ 1457.454300] md0_raid5(178): WRITE block 8 on sdb1 (1 sectors)

```

so maybe this is finished in a few hours?

---

