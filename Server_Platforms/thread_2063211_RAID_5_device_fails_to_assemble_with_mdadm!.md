---
title: "RAID 5 device fails to assemble with mdadm!"
date: 2012-09-26
forum: Server Platforms
---

### Post by tehschulman on 2012-09-26
I've got a file server I've been making an effort to recover for a few weeks now. I first noticed some issues with my disks after a blackout that suddenly powered off the server. I had to do multiple fsck checks on the disks and at one point they were back to their former state, but I assume one of the disks is physically degrading now because of all the additional issues I've run into.

Ever since the blackout, I've been unable to maintain a consistent and stable Ubuntu system. I've been meaning to reformat and reinstall the server for a while, but now with the performance issues I've decided to do this sooner rather than later.

In order to recover my media, I purchased a Network Attached Storage and have been in the process of transfering files over to this backup device. Last night, while transfering some folders, I noticed that the file transfer was having issues with some of the files. Looking closer, I noticed that many of my directories had files that weren't accessible but previously had no issues.

To try and remedy this, I rebooted the system and loaded up the livecd again, but now when I uses mdadm to assemble the two RAID arrays in my server, I get the following message:

```


ubuntu@ubuntu:~$ sudo mdadm --assemble --scan
mdadm: /dev/md0 has been started with 2 drives and 1 spare.
mdadm: failed to add /dev/sdc3 to /dev/md1: Invalid argument
mdadm: failed to add /dev/sdb3 to /dev/md1: Invalid argument
mdadm: failed to add /dev/sda3 to /dev/md1: Invalid argument
mdadm: failed to add /dev/sdd3 to /dev/md1: Invalid argument
mdadm: /dev/md1 assembled from -1 drives and 1 spare - not enough to start the array.
mdadm: failed to add /dev/sdc3 to /dev/md1: Invalid argument
mdadm: failed to add /dev/sdb3 to /dev/md1: Invalid argument
mdadm: failed to add /dev/sda3 to /dev/md1: Invalid argument
mdadm: failed to add /dev/sdd3 to /dev/md1: Invalid argument
mdadm: /dev/md1 assembled from -1 drives and 1 spare - not enough to start the array.


```

/dev/md0 contains my system, but /dev/md1 contains my /home directories and the majority of my media files. Now as it stands, I'm unable to mount or activate my media partition which is set up as a RAID 5 array. Examining the disks in the array returns the following:

```



ubuntu@ubuntu:~$ sudo mdadm -E /dev/sda3
/dev/sda3:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Mon Sep 24 06:49:19 2012
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 4
Preferred Minor : 1

    Update Time : Mon Sep 24 06:55:10 2012
          State : active
 Active Devices : 0
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 4
       Checksum : 9ed4a3cd - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     3       8        3        3      spare   /dev/sda3

   0     0       8       51        0      spare   /dev/sdd3
   1     1       8       35        1      spare   /dev/sdc3
   2     2       8       19        2      spare   /dev/sdb3
   3     3       8        3        3      spare   /dev/sda3


ubuntu@ubuntu:~$ sudo mdadm -E /dev/sdb3
/dev/sdb3:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Mon Sep 24 06:49:19 2012
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 4
Preferred Minor : 1

    Update Time : Mon Sep 24 06:55:10 2012
          State : active
 Active Devices : 0
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 4
       Checksum : 9ed4a3db - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     2       8       19        2      spare   /dev/sdb3

   0     0       8       51        0      spare   /dev/sdd3
   1     1       8       35        1      spare   /dev/sdc3
   2     2       8       19        2      spare   /dev/sdb3
   3     3       8        3        3      spare   /dev/sda3


ubuntu@ubuntu:~$ sudo mdadm -E /dev/sdc3
/dev/sdc3:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Mon Sep 24 06:49:19 2012
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 4
Preferred Minor : 1

    Update Time : Mon Sep 24 06:55:10 2012
          State : active
 Active Devices : 0
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 4
       Checksum : 9ed4a3e9 - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     1       8       35        1      spare   /dev/sdc3

   0     0       8       51        0      spare   /dev/sdd3
   1     1       8       35        1      spare   /dev/sdc3
   2     2       8       19        2      spare   /dev/sdb3
   3     3       8        3        3      spare   /dev/sda3



ubuntu@ubuntu:~$ sudo mdadm -E /dev/sdd3
/dev/sdd3:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Mon Sep 24 06:49:19 2012
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 4
Preferred Minor : 1

    Update Time : Mon Sep 24 06:55:10 2012
          State : active
 Active Devices : 0
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 4
       Checksum : 9ed4a3f7 - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     0       8       51        0      spare   /dev/sdd3

   0     0       8       51        0      spare   /dev/sdd3
   1     1       8       35        1      spare   /dev/sdc3
   2     2       8       19        2      spare   /dev/sdb3
   3     3       8        3        3      spare   /dev/sda3

```

The null UUID bothers me. Am I at the point where I need to buy a new disk and rebuild my array? I've done a few RAID setups in my day but this will be my first hardcore RAID rebuild/recovery. Where should I start?

---

### Post by rubylaser on 2012-09-26
First, I would check all of your disks with smartmontools.
```
apt-get install smartmontools
smartctl -a /dev/sda
```

If they all look healthy with no reallocated sectors, or pending sectors, you can continue.

None of your disks have a mdadm UUID in their superblock and your event counters are back to 1, so you are going to need to re-create the array with the --assume-clean flag to even have a chance of putting this back together. I've only seen this in the case of corruption.  Other forum members have run into this in the past:  [recent]("http://ubuntuforums.org/showthread.php?t=2055557") and [older]("http://ubuntuforums.org/showthread.php?t=1988213"). You have to reassemble in the same order with the same chunk size for this to work.

First, you'll want to stop any running arrays
```
mdadm --stop /dev/md1
```
Then, recreate the array.  
```
mdadm --create /dev/md1 --assume-clean --metadata=0.90 --level=5 --raid-devices=4 /dev/sd[abcd]3
```
If you have a questionable disk (verified by checking smartctl above), you can leave 1 disk out during this assembly. If you do need to leave one out, you need to put the disks in the proper order like this (in this case /dev/sdc is bad).
```
mdadm --create /dev/md1 --assume-clean --metadata=0.90 --level=5 --raid-devices=4 /dev/sda3 /dev/sdb3 missing /dev/sdd3
```

This will use the default chunk size and the order that I assume you used when you created the array. **You have to use the assume clean flag, or you will case a resync a potentially lose all your data.**

---

### Post by tehschulman on 2012-09-27
Hey!

Thank you so much for the reply :D. I ran the smartmontools scan on all of the disks and partitions and they seem healthy according to the tool.

After checking disk integrity I reassembled the array with mdadm and got a message about duplicate arrays on /dev/md1:

```

ubuntu@ubuntu:~$ sudo mdadm --assemble --scan
mdadm: Devices UUID-00000000:00000000:00000000:00000000 and UUID-3cf74e88:ec92d458:e368bf24:bd0fce41 have the same name: /dev/md1
mdadm: Duplicate MD device names in conf file were found.

```

I went into the mdadm.conf and commented out the line for /dev/md1 with the null UUID and then was able to assemble the array:

```

ubuntu@ubuntu:~$ sudo mdadm --assemble --scan
mdadm: excess address on MAIL line: spares=1 - ignored
mdadm: /dev/md0 has been started with 2 drives and 1 spare.
mdadm: /dev/md1 has been started with 3 drives (out of 4).

```

When I tried mounting the device with nautilus I got an error about the file system being the wrong type or there being a bad superblock (no surprise). Syslog had this line in it:

```
[71991.727370] EXT4-fs (md1): bad geometry: block count 1069181904 exceeds size of device (1069181568 blocks)

```

My next thought was to run fsck on /dev/md1, but I got a few warning messages about bad superblocks and fsck wanting to use the original superb locks:

```
ubuntu@ubuntu:~$ sudo fsck.ext4 /dev/md1
e2fsck 1.42 (29-Nov-2011)
fsck.ext4: Group descriptors look bad... trying backup blocks...
fsck.ext4: Bad magic number in super-block when using the backup blocks
fsck.ext4: going back to original superblock
fsck.ext4: Group descriptors look bad... trying backup blocks...
fsck.ext4: Bad magic number in super-block when using the backup blocks
fsck.ext4: going back to original superblock
The filesystem size (according to the superblock) is 1069181904 blocks
The physical size of the device is 1069181568 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? cancelled!


/dev/md1: ********** WARNING: Filesystem still has errors **********


```

Like you said in your first reply, the disks will want to revert to a previous inode, which may end up erasing valuable data (and I want to prevent this of course). I assume I need to now mount /dev/md1 via console, but I'm not sure what options to use now that the superblock is deemed bad. Running a disk check would be a good move forward in my opinion but I'm not sure how to proceed.

Thanks for everything so far! Glad to know I have an extreme case of data corruption but there may be a way out :)

---

### Post by rubylaser on 2012-09-28
Personally, I would try to mount the array first and backup anything that you haven't backed up yet.  I would bet that a mount will fail though, with an unknown filesystem error.  But you could do something as simple as this as a check.

```
mount /dev/md1 /mnt/
```

This will mount your array on /mnt/.  If that works, start the recovery.  If it doesn't work, your only recourse is to run an fsck on the unmounted array, but the message that the original and backup superblocks are bad is disconcerting.

---

### Post by tehschulman on 2013-01-27
Dang it's been a while since I've updated.

Anyhow, I had an adventure in rebuilding the array. The first few times I seem to have put the disks out of order accidentally. The other night though I built the array correctly and added /dev/sdc3 after the build so that the disk would have a fresh slice of the array written to it.

I am still receiving messages about the filesystem superblock not being found. Also when I attempt to mount it complains about not knowing the filesystem type (the partitions are ext4) and also shoots out a bad block magic number error.

Running fsck on the individual partitions return no errors, but I'm still seeing roughly the same error message when I try to fsck /dev/md1/

---

