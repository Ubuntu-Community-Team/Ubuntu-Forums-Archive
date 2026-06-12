---
title: "recovered raid6 array with no fs after recovery"
date: 2010-08-20
forum: Server Platforms
---

### Post by Plecebo on 2010-08-20
I have an 8x1TB raid6 array that I finally got back to a good state (see my other post here: [http://ubuntuforums.org/showthread.php?p=9743829#post9743829](http://ubuntuforums.org/showthread.php?p=9743829#post9743829))

This is on a 9.04 server

Now I can assemble the array no problem, but mounting is the issue. I think the reason might be because the array order changed. 

In the process of recovering I removed the /dev/md0 array and created a new array. In the create array command it told me:
```
mdadm: /dev/sdb1 appears to be part of a raid array:
```
for each device in the array. I confirmed that I wanted to continue and the array was recreated. I think this overwrote the superblock, but I'm not sure. 

After the sync I tried to mount the array using: 
```
mount -r -t ext3 /dev/md0 /mnt/raidarr
```
it tells me: 
```
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

dmesg shows
```
dmesg | tail
[ 3150.147814]  disk 3, o:1, dev:sde1
[ 3150.147817]  disk 4, o:1, dev:sdf1
[ 3150.147820]  disk 5, o:1, dev:sdg1
[ 3150.147824]  disk 6, o:1, dev:sdh1
[ 3150.147827]  disk 7, o:1, dev:sdi1
[ 3150.147987]  md0: unknown partition table
[ 3195.849518] VFS: Can't find ext4 filesystem on dev md0.
[ 3205.351906] VFS: Can't find ext3 filesystem on dev md0.
[ 3879.447329] VFS: Can't find ext3 filesystem on dev md0.
[ 8444.812076] VFS: Can't find ext3 filesystem on dev md0.

```

Here are the details for the array: 
```
 mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Wed Aug 18 01:27:22 2010
     Raid Level : raid6
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Aug 20 10:07:26 2010
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : a0171bb1:c21144bf:73d158fc:63c6b3dd (local to host zeus)
         Events : 0.34

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       5       8       97        5      active sync   /dev/sdg1
       6       8      113        6      active sync   /dev/sdh1
       7       8      129        7      active sync   /dev/sdi1

```

Here is my current mdadm.conf
```
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
ARRAY /dev/md0 level=raid6 num-devices=8 UUID=a0171bb1:c21144bf:73d158fc:63c6b3dd

```

My old mdadm.conf looks like this:
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions /dev/sdf1

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR lme@mydomain.com

# definitions of existing MD arrays

# This file was auto-generated on Fri, 10 Jul 2009 00:30:51 -0700
# by mkconf $Id$
DEVICE /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1
ARRAY /dev/md0 level=raid6 devices=/dev/sdb1,/dev/sdc1,/dev/sdd1,/dev/sde1,/dev/sdf1,/dev/sdg1,/dev/sdh1,/dev/sdi1,/dev/sdf1
MAILFROM me@mydomain.com

```

I guess I'm wondering how to proceed? Should i try to match my old drive order and rebuild the array again? Would this even help get my data back? Especially now that the array is synced with this new order...

I'd love to be able to recover at least some of the data if at all possible.

---

### Post by Plecebo on 2010-08-23
anyone have any suggestions? My main questions are

[LIST=1]
[*]Is there a way to recover the file system on the array without rebuilding the array?
[*]If I have to rebuild the array is there a way I can get a hint as to what the proper order of the array is?
[*]How do I assemble the devices in a specific order?
[*]Any other suggestions that I may not be thinking of?
[/LIST]

Thanks in advance for the help.

---

### Post by rubylaser on 2010-08-23
I'm sorry to hear about the loss of your family photos.  I would be devastated if I lost the photos of my children's births, first steps, etc. I'll try to help you out.  First, what's the output of these two commands.

```
 cat /proc/mdstat
```

```
 mdadm --examine /dev/sdb1
 mdadm --examine /dev/sdc1
 mdadm --examine /dev/sdd1
 mdadm --examine /dev/sde1
 mdadm --examine /dev/sdf1
 mdadm --examine /dev/sdg1
 mdadm --examine /dev/sdh1
 mdadm --examine /dev/sdi1
```

It sounds like it thinks you have /dev/sdb1 in an array by itself, and as a part of this array as well.  Once, I have this info, we can try to continue.  To answer your questions, mdadm will assemble the array with the disks present, regardless of their physical order as long as the superblock is consistent.

And, just so I understand, how many of your original array's disk actually failed?

---

### Post by Plecebo on 2010-08-23
Thanks so much for the help rubylaser. Here is the info you requested. 

> **rubylaser said:**
> First, what's the output of these two commands.

```
 cat /proc/mdstat
```


```
 mdadm --examine /dev/sdb1
 mdadm --examine /dev/sdc1
 mdadm --examine /dev/sdd1
 mdadm --examine /dev/sde1
 mdadm --examine /dev/sdf1
 mdadm --examine /dev/sdg1
 mdadm --examine /dev/sdh1
 mdadm --examine /dev/sdi1
```


```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sdb1[0] sdi1[7] sdh1[6] sdg1[5] sdf1[4] sde1[3] sdd1[2] sdc1[1]
      5860559616 blocks level 6, 64k chunk, algorithm 2 [8/8] [UUUUUUUU]
      
unused devices: <none>

```

/dev/sdb1
```
mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a0171bb1:c21144bf:73d158fc:63c6b3dd (local to host zeus)
  Creation Time : Wed Aug 18 01:27:22 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Fri Aug 20 10:38:35 2010
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b5ff43a3 - correct
         Events : 34

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8      129        7      active sync   /dev/sdi1

```

/dev/sdc1
```
mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a0171bb1:c21144bf:73d158fc:63c6b3dd (local to host zeus)
  Creation Time : Wed Aug 18 01:27:22 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Fri Aug 20 10:38:35 2010
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b5ff43a3 - correct
         Events : 34

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8      129        7      active sync   /dev/sdi1
root@zeus:/home/larry# mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a0171bb1:c21144bf:73d158fc:63c6b3dd (local to host zeus)
  Creation Time : Wed Aug 18 01:27:22 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Fri Aug 20 10:38:35 2010
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b5ff43b5 - correct
         Events : 34

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8      129        7      active sync   /dev/sdi1

```

/dev/sdd1
```
mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a0171bb1:c21144bf:73d158fc:63c6b3dd (local to host zeus)
  Creation Time : Wed Aug 18 01:27:22 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Fri Aug 20 10:38:35 2010
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b5ff43c7 - correct
         Events : 34

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       49        2      active sync   /dev/sdd1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8      129        7      active sync   /dev/sdi1

```

/dev/sde1
```
mdadm --examine /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a0171bb1:c21144bf:73d158fc:63c6b3dd (local to host zeus)
  Creation Time : Wed Aug 18 01:27:22 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Fri Aug 20 10:38:35 2010
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b5ff43d9 - correct
         Events : 34

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       65        3      active sync   /dev/sde1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8      129        7      active sync   /dev/sdi1

```

/dev/sdf1
```
mdadm --examine /dev/sdf1
/dev/sdf1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a0171bb1:c21144bf:73d158fc:63c6b3dd (local to host zeus)
  Creation Time : Wed Aug 18 01:27:22 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Fri Aug 20 10:38:35 2010
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b5ff43eb - correct
         Events : 34

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       81        4      active sync   /dev/sdf1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8      129        7      active sync   /dev/sdi1

```

/dev/sdg1
```
mdadm --examine /dev/sdg1
/dev/sdg1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a0171bb1:c21144bf:73d158fc:63c6b3dd (local to host zeus)
  Creation Time : Wed Aug 18 01:27:22 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Fri Aug 20 10:38:35 2010
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b5ff43fd - correct
         Events : 34

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     5       8       97        5      active sync   /dev/sdg1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8      129        7      active sync   /dev/sdi1

```

/dev/sdh1
```
mdadm --examine /dev/sdh1
/dev/sdh1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a0171bb1:c21144bf:73d158fc:63c6b3dd (local to host zeus)
  Creation Time : Wed Aug 18 01:27:22 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Fri Aug 20 10:38:35 2010
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b5ff440f - correct
         Events : 34

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     6       8      113        6      active sync   /dev/sdh1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8      129        7      active sync   /dev/sdi1

```

/dev/sdi1
```
mdadm --examine /dev/sdi1
/dev/sdi1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a0171bb1:c21144bf:73d158fc:63c6b3dd (local to host zeus)
  Creation Time : Wed Aug 18 01:27:22 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Fri Aug 20 10:38:35 2010
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b5ff4421 - correct
         Events : 34

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     7       8      129        7      active sync   /dev/sdi1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8      129        7      active sync   /dev/sdi1

```

> **rubylaser said:**
> To answer your questions, mdadm will assemble the array with the disks present, regardless of their physical order as long as the superblock is consistent.

And, just so I understand, how many of your original array's disk actually failed?

I'm afraid that I may have somehow overwritten the superblock. I'm not sure what commands will cause the superblock to be changed? 

A brief history. The array originally failed because of an overheat situation (i'm pretty sure). When i examined mdstat it showed all my drives to be spares in the array, which was very strange. I tried to assemble the array several ways but the only way I was successful was to force it to assemble. It then began to re-sync. within the first 20% two of the drives would fail out of the array and cause the re-sync to stop. I tried this several times with the same/similar results. It was not the same two drives that would fail out every time either, but it didn't seem to be ALL of the drives. My guess was that more then two drives were bad and as it was rebuilding a random set of two of the bad drives would fail out causing the array to shutdown. Something to note, even when I was dealing with a re-syncing array with 8 good drives I was not able to get the array to mount, it gave me the bad FS error. At the time I figured it would clear up after syncing, but now i'm not sure that the problem wasn't happening then. 

Anyway, eventually I got frustrated and thought that maybe removing and re-creating the array would be the way to go, so I: 
```
mdadm --remove /dev/md0
mdadm --create /dev/md0 --level=6 --raid-devices=8 /dev/sd{b,c,d,e,f,g,h,i}1

``` 
This code told me that the superblocks were different, and asked if it wanted to proceed... I am afraid I made a mistake in telling it I wanted to proceed. 

Anyway, the array was re-created and the re-sync started up again. Same result, two drives were failed out of the array and it stopped syncing. 

At this point I thought for sure that I had bad drives, and because of the way that it wasn't always the same two drives that failed out of the array, I figured it was more the two bad drives, and that I had lost the data in my array. 

I started trying to identify the drives that had failed, I executed the following commands on each drive. 
```
smartctl -t short /dev/sdb
```
all of these came back ok so I thought to look for badblocks
```
badblocks -sv /dev/sdb1
```
all of these came back ok. 

I thought this was strange, I hadn't been able to identify a single drive that was bad. So I attempted to assemble the array one more time and it synced to 100% and is running the way it is now. It has been running that way for a few days now with no trouble except that I can't mount it. 

Sorry for the long post, but that is the story. 

Thanks again

---

### Post by rubylaser on 2010-08-23
The mdadm create by itself does not wipe out the data. mdadm is smart enough to &#8220;see&#8221; that hard drive belonged to a previous array . Knowing that, mdadm will try to do its best (i.e. if parameters match the previous array configuration) and rebuild the new array upon the previous one in a non-destructive way, by keeping the content.

To zero the superblock, you literally have to pass the --zero-superblock option, so I doubt you did that.  But, even if you did, you should be able to recover the data, if the disks are assembled in the correct order.

The weird thing is that your array eventually correctly synced, you should have had to add disks back like this ( [http://ubuntuforums.org/showthread.php?t=410136]("http://ubuntuforums.org/showthread.php?t=410136") ) to get it to work.

Although, I hate to say this, you might want to do an fsck.ext4 /dev/md0

EDIT:  I don't know how I missed this in your original post...

> In the process of recovering I removed the /dev/md0 array and created a new array. In the create array command it told me:
Code:
```
mdadm: /dev/sdb1 appears to be part of a raid array:
```
for each device in the array. I confirmed that I wanted to continue and the array was recreated. I think this overwrote the superblock, but I'm not sure. 


You did overwrite the superblock with this command.  You would need one disk with the orginal superblock data on it, to repair this problem like I mentioned in the link above. :(

I'm sorry, but I believe your data may be lost at this point.

---

### Post by Plecebo on 2010-08-23
> **rubylaser said:**
> Although, I hate to say this, you might want to do an fsck.ext4 /dev/md0

EDIT:  I don't know how I missed this in your original post...



You did overwrite the superblock with this command.  You would need one disk with the orginal superblock data on it, to repair this problem like I mentioned in the link above. :(

I'm sorry, but I believe your data may be lost at this point.

:( I was afraid of that... 

Running fsck.ext4 gives this error:
```
fsck.ext3 /dev/md0
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext3: Superblock invalid, trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```


So assuming my superblock is overwritten, and assuming I don't know the original drive order, is there a hail mary option? Is it possible for me to "Guess" at the order and have a valid superblock re-created?

I can use the --assume-clean flag so the array doesn't have to rebuild and try to mount the drive. Perhaps even write a script to try all drive order combinations, mount and pipe a "ls" command to a file. then review to see if I can find the right combination.

I guess what I'm asking is the superblock a function of the drive order and if I get the correct drive order again will the superblock be restored? If not that is there any way to recover the superblock?

I really appreciate your help, even if it confirms the bad news I suspected.

---

### Post by rubylaser on 2010-08-23
Well, you wanted a Hail Mary, so here goes...

You could try an alternate superblock..

```
fsck -b 8193 /dev/md0
```

If that fails, you could try mke2fs -n to find the other backup superblocks.

If that doesn't work...
Delete the /etc/mdadm/mdadm.conf file. Then uninstall mdadm.

Reboot.

Re-install mdadm. Then run this command:

```
sudo mdadm --assemble --scan
```
A new .conf file will be created and the array should be back up ready to be mounted (But, I'm not sure if it will work).  

The only other thing you could try is to assemble the array in every possible order, then try to mount it to see if it works.

---

### Post by Plecebo on 2010-08-23
I'll try anything at this point. 

```
fsck -b 8193 /dev/md0
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext3: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

```
mke2fs -n /dev/md0
mke2fs 1.41.4 (27-Jan-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
366288896 inodes, 1465139904 blocks
73256995 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
44713 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848, 512000000, 550731776, 644972544

```

trying these backup superblocks each one gave this result: 
```
fsck -b 644972544 /dev/md0
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext3: Invalid argument while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

renamed mdadm.conf, uninstalled mdadm rebooted, reinstalled mdadm, assembled using mdadm --assemble --scan. 

/dev/md0 was created, but same sittuation when I try to mount it, no file system. 

For assembling the drives in another order, I could probably do this. 

I seem to remember another order of the drives when I ran cat /proc/mdstat in the past. either drive E or F was marked as 0 and the rest followed from that... if I remember correctly

so 
/dev/sd{e,f,g,h,i,b,c,d}1 or /dev/sd{f,g,h,i,b,c,d,e}1

Here is my original mdadm.conf
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions /dev/sdf1

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR me@myaddress.com

# definitions of existing MD arrays

# This file was auto-generated on Fri, 10 Jul 2009 00:30:51 -0700
# by mkconf $Id$
DEVICE /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1
ARRAY /dev/md0 level=raid6 devices=/dev/sdb1,/dev/sdc1,/dev/sdd1,/dev/sde1,/dev/sdf1,/dev/sdg1,/dev/sdh1,/dev/sdi1,/dev/sdf1
MAILFROM me@myaddress.com
```

maybe that "order" would allow the array to mount?

I cant imagine that I would have created my array by putting the drives out of alphabetic order, but I could be wrong I suppose. 

If I assembled the array in a different order, would I be able to mount it and get my data? What is the command to assemble an array in a different order?

Worst case if that would work I could use a script to iterate through all possible combinations of drive order and look for a successful mount. That may take a while to figure it out, but it shouldn't be too complicated.

---

### Post by Vegan on 2010-08-23
I looked over your posts and it looks like some serious damage to the array has happened.

If you cannot get a backup superblock it may be your array is unrecoverable.

It never ceases to amaze me at how many do not backup a RAID array.

---

### Post by rubylaser on 2010-08-23
Vegan, of course a backup would have been ideal. But, backing up a 6TB array is a rather daunting task (cost and time), and at this point is a rather moot anyways, plus it's like pouring salt on an open wound.  I would agree that at this point, it appears that your data is gone.

I'm very sorry that this happened, to you, and hope that you have some physical copies of your photos burned to disc somewhere.

---

### Post by Plecebo on 2010-08-23
> **rubylaser said:**
> Vegan, of course a backup would have been ideal. But, backing up a 6TB array is a rather daunting task (cost and time), and at this point is a rather moot anyways, plus it's like pouring salt on an open wound.  I would agree that at this point, it appears that your data is gone.

I'm very sorry that this happened, to you, and hope that you have some physical copies of your photos burned to disc somewhere.

Thanks for the sympathy. 

One question remains, would assembling the array in a specific order allow me to recover the data?

I actually don't mind figuring a way to brute force my way into the correct order if it will work. 

I suppose I could try it. How does one specify the order to assemble an array in?

I do have a few backups of some of the data on DVD, but I'm missing two years worth of photos and a bunch of documents that were important. 

My strategy will no doubt revise, make no mistake, to include some automated backup process. 

Thanks for your help.

---

### Post by rubylaser on 2010-08-23
Unfortunately, based on the array was created and "forced" back together, the old superblocks don't exist, so it doesn't know how to assemble it the old way.  At this point the data is gone.  I personally have a colo-located server that I rsync my photos and home videos to. And every 3 months, I also burn all of this data to DVD9's and store it in the fire safe at work.  That way I have a backup in multiple places, and prevent silent data corruption with the burned discs.

---

### Post by Plecebo on 2010-08-23
Well thanks everyone for the information and help, I guess that is that.

---

