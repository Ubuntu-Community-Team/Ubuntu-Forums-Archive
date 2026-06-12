---
title: "Degraded Raid5"
date: 2012-09-09
forum: Server Platforms
---

### Post by chj-se on 2012-09-09
For a while I have wanted to break the raidset that I have, and use some type of JBOD setup, as I do not require redundancy. And then I had a possibility, as one of the drives actually died. 

I have 4 x 1.5 TB drives in a RAID5. I have force mounted 3 of the 4 drives, and the raid set is clean.

Getting the raid online:
```
mdadm --assemble --force /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sde1 /dev/sdd1
```

Once the raidset was online, I offloaded data, I now have less than 1.3 TB of data (should fit on one drive)

I have run a e2fsck -f /dev/md and have a good file system. I then ran resize2fs to resize the md0 filesystem to 1.3 TB 

I have tried to run a grow on the md0 set, but nothing happens.

Grow Command, and nothing happens:
```
mdadm --grow /dev/md0 --size=138412032
```

Current mdstat:
```
cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[0] sdd1[3] sde1[2]
      4152360960 blocks level 5, 64k chunk, algorithm 2 [4/3] [U_UU]

```

Details of /dev/md0:
```
mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Fri Apr  8 12:39:06 2011
     Raid Level : raid5
     Array Size : 4152360960 (3960.00 GiB 4252.02 GB)
  Used Dev Size : 1384120320 (1320.00 GiB 1417.34 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Sep  9 11:34:27 2012
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 3ce16aed:03b66e97:272fb3ce:18a82fda
         Events : 0.310190

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed
       2       8       65        2      active sync   /dev/sde1
       3       8       49        3      active sync   /dev/sdd1

```

What I need help with is:
Get the current raidset to work with 3 drives and resynced, so that I can forcefully remove 1 drive, format it and then offload the remaining data.

FYI:
The missing drive, the one that went offline is /dev/sdc1, this was tested, formated and used to offload data already.

---

### Post by rubylaser on 2012-09-09
You already have one disk removed from your RAID5 array, so your array is already degraded.  You are not going to be able to remove another disk from the array without breaking it completely.  I would purchase 1 2TB drive to offload your remaining data safely. This is the safest way to do this migration and the least likely to cause data loss (and you'll have a disk to  use for backup).

Once your data is backed up, if you don't require redundancy I would stop the array, zero the superblocks on the remaining disks, and remove your /etc/mdadm/mdadm.conf file and run update-initramfs -u to remove all traces of your array.

If you still want to have one big volume to write to, but that can operate as individual disks, you should take a look at [mhddfs]("http://romanrm.ru/en/mhddfs"). Also, you need to put a backup strategy in place, because at some point, you will lose a disk and losing 1.5TB+ of data would be heartbreaking.

---

### Post by chj-se on 2012-09-09
Yes, the plan is to use MHDDFS, and yes, I will be crying when I lose the data. But it is either to build a new server from sratch to get space for additional disks, or buy new drives all in all.

Isn't it possible to go from a 4 drive RAID5 to a 3 drive RAID5 (or any other RAID level) and still keep the data. I am willing to risk the data that is left, but hope to aviod crying already today.

As noted the data on the drive is less than one single drive. Buying a new drive is of course an option, but a lousy one, as I then need to connect via USB or similar as the "server" is currently full! (No power, SATA or chassie space available.)

---

### Post by chj-se on 2012-09-09
Ok, I solved the issue. Thanks to even more googeling.

Installing an experimental version of mdadm, allows the removal of a drive.

***NOTE:*** This is an **experimental **case, so please do not run if **_you are not willing to risk data_**.

**Links:**
[Blog Post with Howto]("http://blog.stalkr.net/2009/10/reducing-number-of-devices-in-raid-5.html")
[Ubuntu forum post about upgrading]("http://ubuntuforums.org/showthread.php?t=1395450")
[Debian Package for mdadm]("http://packages.debian.org/unstable/admin/mdadm")

Here is my way forward:
1. 4 Drives in RAID5, drive failed
2. Forced 3 of 4 drives online
3. Copied out data leaving only 1.3 TB on degraded RAID5
4. Resized /dev/md0 to 1.3TB instead of 4 TB
5. Installed mdadm experimental

```

# wget http://ftp.se.debian.org/debian/pool/main/m/mdadm/mdadm_3.2.5-3_i386.deb

#dpkg -i mdadm_3.2.5-3_i386.deb

# mdadm --version
mdadm - v3.2.5 - 18th May 2012

```

6. Resize Array
```
# mdadm /dev/md0 --grow --array-size=1385120320

# mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Fri Apr  8 12:39:06 2011
     Raid Level : raid5
     Array Size : 1385120320 (1320.95 GiB 1418.36 GB)
  Used Dev Size : 1384120320 (1320.00 GiB 1417.34 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Sep  9 12:46:27 2012
          State : clean, degraded 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 3ce16aed:03b66e97:272fb3ce:18a82fda
         Events : 0.310204

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed
       2       8       65        2      active sync   /dev/sde1
       3       8       49        3      active sync   /dev/sdd1

```

7. Decrease number of drives
```
# mdadm /dev/md0 --grow  --raid-devices=3 --backup-file=/tmp/mdadm.backup
mdadm: Need to backup 384K of critical section..
```

8. View new raid set
```
# mdadm --detail /dev/md0
/dev/md0:
        Version : 0.91
  Creation Time : Fri Apr  8 12:39:06 2011
     Raid Level : raid5
     Array Size : 1385120320 (1320.95 GiB 1418.36 GB)
  Used Dev Size : 1384120320 (1320.00 GiB 1417.34 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Sep  9 14:03:55 2012
          State : clean, degraded, reshaping
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

 Reshape Status : 0% complete
  Delta Devices : -1, (4->3)

           UUID : 3ce16aed:03b66e97:272fb3ce:18a82fda
         Events : 0.310214

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed
       2       8       65        2      active sync   /dev/sde1

       3       8       49        3      active sync   /dev/sdd1
```

8. Monitor progress
```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdb1[0] sdd1[3] sde1[2]
      1385120320 blocks super 0.91 level 5, 64k chunk, algorithm 2 [3/2] [U_U]
      [>....................]  reshape =  0.0% (476800/1384120320) finish=3005.5min speed=7672K/sec

```

Now I just need to wait for 50 hours for the reshape to be done! Data is accessable still, so lets hope that nothing kills the data on the drive.

---

### Post by rubylaser on 2012-09-09
This whole post doesn't make sense.  You could have easily done this with the version of mdadm that ships with 12.04.  I thought you wanted to move away from mdadm because you didn't need redundancy.  I'm glad you got it figured out, although I would have been happy to help you if your original post  would have stated that you just wanted to reduce the number of disks in your mdadm array by one.  I think buying a new hard drive to migrate my important data rather than a risky filesystem size reduction, followed by a 50 hour RAID5 reshape would have been the safer way to handle this migration.

---

### Post by chj-se on 2012-09-09
I do want to move away from the RAID, but still need to get the data off the raid before I destory it.

I thought I was quite clear with my question:
> What I need help with is:
Get the current raidset to work with 3 drives and resynced, so that I can forcefully remove 1 drive, format it and then offload the remaining data.

Sorry, didn't say that the server is running 10.04 LTS, so the built in mdadm did not support removal of 1 device.

But hey, all is well, that end well. 

Thanks anyways.

---

