---
title: "RAID members only exist in 8.04, not 8.10"
date: 2009-02-16
forum: Server Platforms
---

### Post by Kilbasar on 2009-02-16
Hi guys, thanks for taking the time to help. I have a RAID5 array, used for media, previous running under 8.04. I wanted a clean start, so I wiped my "/" partition (on a separate disk from the RAID5) and re-installed with 8.10. When I first booted up after installing mdadm, it "found" my array, but said it was degraded and tried to rebuild the 3rd disk. Since then, the array appears clean, but won't mount:

```
# sudo mdadm --detail /dev/md0 
/dev/md0:
        Version : 00.90
  Creation Time : Wed Apr  2 16:08:44 2008
     Raid Level : raid5
     Array Size : 1465148928 (1397.27 GiB 1500.31 GB)
  Used Dev Size : 732574464 (698.64 GiB 750.16 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Feb  9 19:47:20 2009
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 28ce99d8:12dc7f14:80dcd6ba:f1e671fb
         Events : 0.22

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       8       64        2      active sync   /dev/sde

# sudo mdadm --detail --scan
ARRAY /dev/md0 level=raid5 num-devices=3 metadata=00.90 UUID=28ce99d8:12dc7f14:80dcd6ba:f1e671fb

# sudo fdisk -l /dev/md0

Disk /dev/md0: 1500.3 GB, 1500312502272 bytes
255 heads, 63 sectors/track, 182402 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009860b

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1       91201   732572001   fd  Linux raid autodetect

# sudo mount -t ext3 /dev/md0 /raid
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
# dmesg|tail -1
[118517.394256] VFS: Can't find ext3 filesystem on dev md0.
```

The strange thing is, if I boot into an 8.04 LiveCD and install mdadm, I can assemble my array ("mdadm --assemble --scan"), and the ext3 partition shows up and mounts without problems. Here's what I see while on the 8.04 LiveCD:

```
# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Wed Apr  2 20:21:23 2008
     Raid Level : raid5
     Array Size : 1465143808 (1397.27 GiB 1500.31 GB)
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Feb 17 01:19:29 2009
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : dbdec02d:c53e6535:80dcd6ba:f1e671fb
         Events : 0.62

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       0        0        2      removed

# fdisk -l /dev/md0

Disk /dev/md0: 1500.3 GB, 1500307259392 bytes
2 heads, 4 sectors/track, 366285952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

# mdadm --detail --brief /dev/md0
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=dbdec02d:c53e6535:80dcd6ba:f1e671fb
```

As you probably noticed, the major difference between 8.04 (where it works) and 8.10 (where it doesn't) is that 8.04 is building the array with sdb1 and sdc1, while 8.10 is building it with sdb and sdc (and sde). And in fact sdb1 and sdc1 don't exist in my 8.10 system:

```

# mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1
mdadm: cannot open device /dev/sdb1: No such file or directory
mdadm: /dev/sdb1 has no superblock - assembly aborted

# ls /dev/sd*
/dev/sda   /dev/sdb  /dev/sdd   /dev/sdd2  /dev/sdd5  /dev/sdf   /dev/sdg  /dev/sdi
/dev/sda1  /dev/sdc  /dev/sdd1  /dev/sdd3  /dev/sde   /dev/sdf1  /dev/sdh  /dev/sdj

```

Why can't I see these partitions under 8.04? This whole thing has me pretty confused...

---

### Post by bapoumba on 2009-02-17
Moved to Servers, and bump.

---

### Post by fjgaude on 2009-02-17
Okay, we've seen this before. Here's what I'd do, exactly: delete or rename **mdadm.conf** file. purge **mdadm** using **apt-get**, re-boot. Install mdadm and run this command:

```
sudo mdadm --assemble --scan
```

A new mdadm.conf file will be created and all should be okay.

Let us know how things go.

---

### Post by Kilbasar on 2009-02-17
Hi, thanks for the suggestion. I will definitely try that. However, because the last time I installed mdadm under 8.10 it seemingly zapped my third drive, I am first going to do a full backup of this data to external media (from inside the LiveCD). Afterwards I will try your suggestion, so it might be a day or two before I get the chance. I will report back here afterwards.

---

### Post by Kilbasar on 2009-02-18
So, after backing up all my data, I gave this a try. And it seems to have worked! After re-installing mdadm, i ran "mdadm --assemble --scan", and it built a functioning array out of sdb1 and sdc1, just as on the LiveCD. So now I just need to get sde back into it, so I have some fault tolerance again. For some reason, it still only sees "/dev/sde", not "sde1", but I was able to add "sde" to the array, and it's building:

```
# mdadm /dev/md0 --add /dev/sde1
mdadm: cannot find /dev/sde1: No such file or directory
# mdadm /dev/md0 --add /dev/sde
mdadm: added /dev/sde
# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Wed Apr  2 16:21:23 2008
     Raid Level : raid5
     Array Size : 1465143808 (1397.27 GiB 1500.31 GB)
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Feb 18 20:11:53 2009
          State : clean, degraded, recovering
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 0% complete

           UUID : dbdec02d:c53e6535:80dcd6ba:f1e671fb
         Events : 0.5910

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       3       8       64        2      spare rebuilding   /dev/sde

```

Possibly once it's done building, the partition will show up? I would like to be certain that I can still lose a drive and get my data back. If I "--fail" a drive, to simulate a problem, can I then re-add it without having to rebuild the data?

---

### Post by fjgaude on 2009-02-18
Well, I'm not sure how to answer... the /sde versus /sde1 is a mystery. I've never seen such a thing before. I've either made all drives without partitions or had them all with one partition, during the --create process.

If you -f a drive, then -r it, and then -a it back I think, remember it comes back as a spare. Just can't remember for sure. You may have to --grow the array from 2 to 3 drives.

The re-build is a normal thing... you can watch it with:

```
sudo watch cat /proc/mdstat
```

I do believe you can use the array while it is rebuilding. These things don't happen often enough for me to even remember.

I always have triple backups of all important data using **Unison** and **Grsync**, so when things have gone "bad", I just re-create the array, after -f and -r each drive, stopping the array, unmounting it, and then zero-superblock on each drive. That's the only way to re-make a new array from old drives. Be warned! Make backups, period.

Let us know how and what you are doing.

---

### Post by Kilbasar on 2009-02-19
My guess is that during the funny period when mdadm was broken, it directly wrote to the drive because it did not see the partition on the disk. So once I got things worked out, the partition there had been overwritten and destroyed.

I'm not sure whether mdadm really "needs" there to be partitions on the disks, if you're using the entire disk anyway. Most likely it would work properly either way. But I like things to be consistent, so I did:

```
# mdadm --manage /dev/md0 --fail /dev/sde
mdadm: set /dev/sde faulty in /dev/md0
# mdadm --manage /dev/md0 --remove /dev/sde
mdadm: hot removed /dev/sde
# fdisk -l /dev/sde

Disk /dev/sde: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sde doesn't contain a valid partition table
```

As you can see, there is no valid partition. So I fired up fdisk, created a new partition, set it to type "fd linux auto-raid", and re-added it to the partition, this time as sde1:

```
# fdisk -l /dev/sde

Disk /dev/sde: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x971bc09c

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       91201   732572001   fd  Linux raid autodetect
# mdadm /dev/md0 --add /dev/sde1
mdadm: added /dev/sde1

```

It is now re-building sde1. Once that completes, I will test it out by failing either sdb1 or sdc1. If it really rebuilt sde1 properly, I should still be able to run my array, and I can stop worrying that mdadm will suddenly leave my array in, ahem, disarray ;)

---

### Post by fjgaude on 2009-02-19
Well, as you likely know **fdisk** doesn't understand raid disks... I think that is changing though.

I've created arrays with no partitions as well as with. Both work fine. Now with no partition, not even one on a drive, fdisk will say there is no valid partition on the drive.

If you create an array with no partition, then do a **mkfs** on the array I don't think fdisk has a clue.

Let us know how your testing does. Years ago, before committing to mdadm, I ran all kinds of tests on various arrays, raid1, raid5, from two to five drives. Had lots of fun learning to use **mdadm**... I was satisfied I could get out of any troubles that hardware failures would present, even motherboard failues. <smile>

Good luck...

---

### Post by Kilbasar on 2009-02-19
Yes, fdisk doesn't understand anything that's going on inside the partition, and I don't think mdadm cares whether or not there's a partition. The only advantage I can think of to using partitions is if maybe one of my 750gb drives dies, I could replace it with a 1tb drive. Since I would only be using 750gb on the new drive (until I was able to upgrade all 3 to 1tb), with partitions I could have a 750gb partition for use in the RAID, and have a 250gb non-RAID partition for other purposes. Or really any situation where you have drives of unequal size. But when using the full drive capacity for RAID, partition or non-partition doesn't really matter.

As for why I set up partitions in the first place, it was a while ago, but many of the mdadm guides I had read included the partitioning step, so what the hell. It also makes it more obvious what the drive is used for, for instance if you have otherwise identical drives and haven't labeled which ones are used for RAID.

---

### Post by fjgaude on 2009-02-19
Well, mostly I used the whole drive and made one partition out of it. Sometimes I've forgotten to set the drives to "fd" without ever seeing that it made any difference. I'm sure it does in certain situations, but for me it never has.

For me, from here on out, I'll aways have one partition so that if a drive needs replacing I can partition the new drive to the same size as the others in an array.

Have fun with your computers...

---

### Post by _kaizer on 2009-02-19
Case closed?

---

### Post by Kilbasar on 2009-02-20
GAAAA!

I rebooted my machine, and now I'm back to my original situation. The partitions are still there (fdisk sees them), but they do not show up in the filesystem, and the array will not mount. This must be a bug, and I really don't know what to do at this point.

```

# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Wed Apr  2 16:08:44 2008
     Raid Level : raid5
     Array Size : 1465148928 (1397.27 GiB 1500.31 GB)
  Used Dev Size : 732574464 (698.64 GiB 750.16 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Feb 20 12:09:19 2009
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 28ce99d8:12dc7f14:80dcd6ba:f1e671fb
         Events : 0.24

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       0        0        2      removed
# fdisk -l /dev/sdb

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009860b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   fd  Linux raid autodetect
# fdisk -l /dev/sde

Disk /dev/sde: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x971bc09c

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       91201   732572001   fd  Linux raid autodetect
# fdisk -l /dev/sdc

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf66d8789

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001   fd  Linux raid autodetect
# mdadm --stop /dev/md0
mdadm: stopped /dev/md0
# mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sde1
mdadm: cannot open device /dev/sdb1: No such file or directory
mdadm: /dev/sdb1 has no superblock - assembly aborted
# mdadm --examine /dev/sdb1
mdadm: cannot open /dev/sdb1: No such file or directory
# mdadm --examine /dev/sdb
/dev/sdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 28ce99d8:12dc7f14:80dcd6ba:f1e671fb
  Creation Time : Wed Apr  2 16:08:44 2008
     Raid Level : raid5
  Used Dev Size : 732574464 (698.64 GiB 750.16 GB)
     Array Size : 1465148928 (1397.27 GiB 1500.31 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0

    Update Time : Fri Feb 20 12:13:35 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 14d7b144 - correct
         Events : 26

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       16        0      active sync   /dev/sdb

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       0        0        2      faulty removed

# ls /dev/sd*
/dev/sda   /dev/sdb  /dev/sdd   /dev/sdd2  /dev/sdd5  /dev/sdf  /dev/sdh
/dev/sda1  /dev/sdc  /dev/sdd1  /dev/sdd3  /dev/sde   /dev/sdg  /dev/sdi

```

I can't see any way that this is anything other than a bug in mdadm. :(

---

### Post by fjgaude on 2009-02-20
Let's see. You removed a drive, physcially? Without mdamd's -f and -r command first? Then rebooted and you a belly-up, dead in the water?

Let's see what your mdadm.conf file looks like now, please.

Also what version of **mdadm** are you using?

```
mdadm --version
```

---

### Post by Kilbasar on 2009-02-20
Nope, I did not remove or fail anything. I simply rebooted my computer, that's the only thing that changed between it working and non-working.

```

# mdadm --version
mdadm - v2.6.7 - 6th June 2008
# cat /etc/mdadm/mdadm.conf 
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
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=dbdec02d:c53e6535:80dcd6ba:f1e671fb
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=28ce99d8:12dc7f14:80dcd6ba:f1e671fb

# This file was auto-generated on Wed, 18 Feb 2009 20:02:09 -0500
# by mkconf $Id$

```

That was what it looked like upon initial reboot. That first ARRAY line doesn't work (despite being the one in use when the array was working properly), as assembling the array with this config leads to:

```
# mdadm --assemble /dev/md0
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.

```

It assembles the array using JUST /dev/sdb. If I comment out the first ARRAY line and use the second one, it puts me back where I was originally, with a "clean" (but unmountable) array composed of sdb and sdc (with one "removed"), and the --detail output given above.

---

### Post by fjgaude on 2009-02-20
Well, this means that the three drives do not have the same UUID... I've have to think about what to do... I've never seen this work out without re-doing the array.

Re-doing the array is starting over, completely. That means zero-superblock of each drive and using --create to make a new array from the old drives. It's the only to use drives that have been in an array in a new array.

Let us know what you are doing.

---

### Post by Kilbasar on 2009-02-20
Yeah, it appears that booting up with mdadm installed causes sdb1, sdc1, and sde1 to somehow disappear. I once again un-installed mdadm, then rebooted. With mdadm NOT installed, I could see sdb1, sdc1, and sde1. I then installed mdadm, and was able to assemble the array using the partitions ("mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sde1"), with everything working:

```
# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Wed Apr  2 16:21:23 2008
     Raid Level : raid5
     Array Size : 1465143808 (1397.27 GiB 1500.31 GB)
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Feb 20 13:58:32 2009
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : dbdec02d:c53e6535:80dcd6ba:f1e671fb
         Events : 0.5962

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       65        2      active sync   /dev/sde1

# cat /etc/mdadm/mdadm.conf
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
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=28ce99d8:12dc7f14:80dcd6ba:f1e671fb
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=dbdec02d:c53e6535:80dcd6ba:f1e671fb

# This file was auto-generated on Fri, 20 Feb 2009 13:57:25 -0500
# by mkconf $Id$

# mdadm --detail --brief /dev/md0
ARRAY /dev/md0 level=raid5 num-devices=3 metadata=00.90 UUID=dbdec02d:c53e6535:80dcd6ba:f1e671fb

```

After I reboot my computer, sdb1 sdc1 and sde1 no longer appear in my file system (although fdisk can see them on the disks), and the array is no longer mountable:

```
# cat /etc/mdadm/mdadm.conf
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
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=28ce99d8:12dc7f14:80dcd6ba:f1e671fb
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=dbdec02d:c53e6535:80dcd6ba:f1e671fb

# This file was auto-generated on Fri, 20 Feb 2009 13:57:25 -0500
# by mkconf $Id$

# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Wed Apr  2 16:08:44 2008
     Raid Level : raid5
     Array Size : 1465148928 (1397.27 GiB 1500.31 GB)
  Used Dev Size : 732574464 (698.64 GiB 750.16 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Feb 20 14:02:49 2009
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 28ce99d8:12dc7f14:80dcd6ba:f1e671fb
         Events : 0.34

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       0        0        2      removed

# mdadm --detail --brief /dev/md0
ARRAY /dev/md0 level=raid5 num-devices=3 metadata=00.90 UUID=28ce99d8:12dc7f14:80dcd6ba:f1e671fb

```

In addition to the partitions disappearing, the UUID of the array has changed. If I try to force it to use the old UUID, I get:

```
# mdadm --assemble /dev/md0 --uuid=dbdec02d:c53e6535:80dcd6ba:f1e671fb
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.
# mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sde[2](S)
      732574464 blocks
       
unused devices: <none>

```

The same thing happens if I comment out the first ARRAY line in mdadm.conf. Commenting out the second line instead results in the same thing as having neither one commented out (2 drives in array, not using partitions).

---

### Post by Kilbasar on 2009-02-20
This has got to be a bug, but at this point I don't care, I just want to be back up and running. I've already backed up all the data to an external drive, so I'm a-okay with zeroing the superblocks and starting from scratch. I don't think I'll use partitions this time. What commands would you recommend for zeroing the superblocks and starting the array fresh? Thanks!

---

### Post by fjgaude on 2009-02-20
First, stop the array. Then do this for each drive of the array:

```
sudo mdadm zero-superblock /dev/sd[nn]
```

Then use the --create command to make a new array. It's all in the **man** pages for **mdadm**.

---

### Post by Kilbasar on 2009-02-22
I zeroed the superblocks, deleted the partitions, then re-created the RAID5, directly on the disks. Currently I am copying the data back over onto the RAID5, then will do a couple of reboots to ensure it is working properly. Thanks for your help.

I have opened a bug report for this issue on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/332235](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/332235)

---

### Post by fjgaude on 2009-02-22
Good luck with the bug report... it's hard to understand how the author will go about fixing whatever is wrong... we can have hope, eh?

You did **mkfs** on the created array before you started copying files to it? Sure you must have!

---

### Post by Kilbasar on 2009-03-08
Just wanted to follow up and say that I have had no further issues with my RAID after re-making it. Of course, the only way to truly test it would be to re-install my system again. Maybe at some point I will try pulling out a drive, when I have a couple hours free to deal with the results. Until then, I'll just make sure my backup script is up to snuff ;)

---

### Post by fjgaude on 2009-03-08
Great! Let us know of your adventures. Thanks.

---

