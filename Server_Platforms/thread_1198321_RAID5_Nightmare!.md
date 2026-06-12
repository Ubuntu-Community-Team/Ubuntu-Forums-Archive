---
title: "RAID5 Nightmare!"
date: 2009-06-27
forum: Server Platforms
---

### Post by joshlos on 2009-06-27
Just read through tutorials to create an mdadm raid5 out of 4 1.5 TB harddrives. Used fdisk to create 4 raid partitions, used the following command:

```
mdadm -C /dev/md0 -n4 /dev/sd[cdef]1 -l5
```

Then made a filesystem for the new raid device with fdisk (ext3).

Rebooted, now the nightmare begins. Tried to reassemble it, seems to work, only now it thinks one drive is a spare, one drive is failed, and it seems to have removed some things:

```
root@usmanbux99200:/raid/home1/josh# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sde1[2] sdc1[4](F) sdd1[1] sdf1[5](S)
      4395407808 blocks level 5, 64k chunk, algorithm 2 [4/2] [_UU_]
      
unused devices: <none>
```

```
root@usmanbux99200:/raid/home1/josh# mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Fri Jun 26 23:14:37 2009
     Raid Level : raid5
     Array Size : 4395407808 (4191.79 GiB 4500.90 GB)
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Jun 27 10:12:56 2009
          State : clean, degraded
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 1317d5fc:94d35201:0d1ad50b:b32cafd2 (local to host usmanbux99200)
         Events : 0.96

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       49        1      active sync   /dev/sdd1
       2       8       65        2      active sync   /dev/sde1
       3       0        0        3      removed

       4       8       33        -      faulty spare   /dev/sdc1
       5       8       81        -      spare   /dev/sdf1

```

and..

```
root@usmanbux99200:/raid/home1/josh# mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1317d5fc:94d35201:0d1ad50b:b32cafd2 (local to host usmanbux99200)
  Creation Time : Fri Jun 26 23:14:37 2009
     Raid Level : raid5
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
     Array Size : 4395407808 (4191.79 GiB 4500.90 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sat Jun 27 10:02:39 2009
          State : active
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1
       Checksum : fd3ee65f - correct
         Events : 87

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       33        0      active sync   /dev/sdc1

   0     0       8       33        0      active sync   /dev/sdc1
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       0        0        3      faulty removed
   4     4       8       81        4      spare   /dev/sdf1

```
[B]
Please help me![/B]

---

### Post by Boondoklife on 2009-07-03
Are you sure the partitions are exaclty the same size? I had and instance with 3 drives same make etc but one of them was like 22 blocks short. Try to cut 50MB off the partitions and try again.

---

### Post by fjgaude on 2009-07-06
Well, **mdadm** creates arrays using the size of the smallest partition. So the sizes are not the issues.

Sounds like the drives or partitions have been used in software arrays before. Is this so?

---

### Post by joshlos on 2009-07-07
> **fjgaude said:**
> Well, **mdadm** creates arrays using the size of the smallest partition. So the sizes are not the issues.

Sounds like the drives or partitions have been used in software arrays before. Is this so?

Hmm.. well I tried to mdadm twice. The first time I ran into a different set of issues, so I formatted them all and reconfigured them with mdadm.

Still having issues; any ideas?

Thanks!

---

### Post by drave99 on 2009-07-07
id say start over BUT ...when re-using disks make sure you clear the superblock (mdadm --zero-superblock) or it can get its knickers in a twist. mdadm --examine should just say "No superblock detected"

on my system once it been created, it took > 1 day to finish syncing itself. could be that if you rebooted during this period who knows ... (why reboot ?)

and ive never had to assemble it, it just works

---

### Post by joshlos on 2009-07-07
Thanks a bunch... I will try this. Does anyone have a good, technical overview of the way mdadm runs a RAID5? Might help me understand some of these problems better.

---

### Post by joshlos on 2009-07-07
Okay, so I started over with a fresh mdadm install, formatted drives with zeroed superblocks (mdadm --zero-superblock) and fresh fdisk "fd" partitions.

same mdadm -C command from before, level 5 with 4 1.5tb drives (sdc through sdf).

Seems to be syncing, but my problem right now is the following: when I examine the RAID (mdadm --examine /dev/md0), device "3", which is blank, shows up as "faulty", and device "4", /dev/sdf1, shows up as a spare. shouldn't all four of these drives show up as "active sync"? I want a 4.5 TB array with one drive 'redundant'. Here's the output:

```
root@usmanbux99200:~# mdadm --examine /dev/sdf1
/dev/sdf1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 84012259:3cbdaeb4:0d1ad50b:b32cafd2 (local to host usmanbux99200)
  Creation Time : Tue Jul  7 20:47:54 2009
     Raid Level : raid5
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
     Array Size : 4395407808 (4191.79 GiB 4500.90 GB)
   Raid Devices : 4
  Total Devices : 5
Preferred Minor : 0

    Update Time : Tue Jul  7 20:47:54 2009
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 162eb39e - correct
         Events : 1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       81        4      spare   /dev/sdf1

   0     0       8       33        0      active sync   /dev/sdc1
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       0        0        3      faulty
   4     4       8       81        4      spare   /dev/sdf1

```

Any ideas?

---

### Post by drave99 on 2009-07-08
i just did the same on a test system here and got exactly the same result WHILE the raid was building/syncing. after it had finished everything looks fine. 

who knows whats going on but it is all A.OK

---

### Post by fjgaude on 2009-07-08
I can't say what's going on. You have five drives in the array but you only created the array with four?

It would seem that **mdadm** still thinks five are part of the array. After array creation did you add the additional drive?

What does your **/etc/mdadm/mdadm.conf** file show?

Here's a link that might be useful:

[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)

Let us know what you learn.

---

### Post by joshlos on 2009-07-08
Well, this is all very strange, but it would appear that the array is now working. Here's what I did:

I declared the "spare" drive faulty and removed it, then re-insterted it into the array ("hot" add).

After doing this and checking /proc/mdstat, it said that the array was "recovering" and it would take about 10 hours.

Woke up this morning and checked mdadm --examine, and it looks like all four drives are in perfect order, and the raid partition mounted like a charm.

Not sure that I figured out what exactly was the problem, but it would appear to be fixed.

Thanks for all the help!

---

### Post by fjgaude on 2009-07-08
Wow, good news!

You can use this to watch an array assemble:

```
sudo watch cat /proc/mdstat
```

Super way to know what's going on. Sometimes I think many problems are caused when we don't let an array fully get formatted or assembled before we start using it.

---

### Post by joshlos on 2009-07-09
This just keeps getting better. So the array WAS working, and then...

My computer was acting up last night, declaring some file systems (on my raid 5 array) as "read only" and intermittently hanging for a few seconds here and there.

So I restarted the machine, which greeted me with "i/o" errors on one of my raid partitions.. /dev/sdf1. It took about 5 minutes of errors, but ubuntu finally showed up, and (as has become not much of a surprise to me these days) my RAID is not working again!

```
root@nessy:~# mdadm --examine /dev/md0
mdadm: No md superblock detected on /dev/md0.
root@nessy:~# mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 84012259:3cbdaeb4:0d1ad50b:b32cafd2
  Creation Time : Tue Jul  7 20:47:54 2009
     Raid Level : raid5
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
     Array Size : 4395407808 (4191.79 GiB 4500.90 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Jul  8 22:32:59 2009
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 16301d9b - correct
         Events : 21

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       33        0      active sync   /dev/sdc1

   0     0       8       33        0      active sync   /dev/sdc1
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       81        3      active sync   /dev/sdf1
root@nessy:~# mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 84012259:3cbdaeb4:0d1ad50b:b32cafd2
  Creation Time : Tue Jul  7 20:47:54 2009
     Raid Level : raid5
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
     Array Size : 4395407808 (4191.79 GiB 4500.90 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Jul  8 22:54:57 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 1630295d - correct
         Events : 836

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       49        1      active sync   /dev/sdd1

   0     0       0        0        0      removed
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       0        0        3      faulty removed
root@nessy:~# mdadm --examine /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 84012259:3cbdaeb4:0d1ad50b:b32cafd2
  Creation Time : Tue Jul  7 20:47:54 2009
     Raid Level : raid5
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
     Array Size : 4395407808 (4191.79 GiB 4500.90 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Jul  8 22:54:57 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 1630296f - correct
         Events : 836

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       65        2      active sync   /dev/sde1

   0     0       0        0        0      removed
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       0        0        3      faulty removed
root@nessy:~# mdadm --examine /dev/sdf1
/dev/sdf1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 84012259:3cbdaeb4:0d1ad50b:b32cafd2
  Creation Time : Tue Jul  7 20:47:54 2009
     Raid Level : raid5
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
     Array Size : 4395407808 (4191.79 GiB 4500.90 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Jul  8 22:53:37 2009
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 1630247c - correct
         Events : 481

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       81        3      active sync   /dev/sdf1

   0     0       0        0        0      removed
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       81        3      active sync   /dev/sdf1

```

I'm about done with this B.S. software raid. My time is valuable, the data is even more valuable, and I think I'm going to spring for a hardware RAID solution.

Has anyone had success with LSI MegaRAID 300 on linux? It appears from the site that this card has full linux support.

---

### Post by fjgaude on 2009-07-09
Look, many of us have been using **mdadm** for years and it is solid. Much hardware that we use is not.

I've had lots of issues with drives, especially Seagate, the big ones.

As a last effort what does this command show:

```
sudo mdadm -D /dev/md0
```

This is the one to use on the whole array, not -E.

How does the UUID compare with what is in the **/etc/mdadm/mdadm.conf** file? All drives should have the same UUID. This is not the UUID one uses to mount drives, but is unique to arrays and how they are auto assembled.

Any hardware raid card you buy, unless you spend over $300 for it, will be slower, much slower, than mdadm.

---

### Post by joshlos on 2009-07-09
I cant make the /dev/md0 active anymore, so mdadm-D /dev/md0 doesn't return anything helpful.

So I have 4x 1.5 TB Seagate drives. Do they not play nicely with mdadm? Is it a firmware issue?


=====
So I just ran fsck on md0, and it tells me that it may be corrupt now:
[CODE]root@nessy:~# fsck /dev/md0
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext3: Invalid argument while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

[\CODE]

---

### Post by fjgaude on 2009-07-09
Well, one or more of the drives could have failed... I can't say.

I had six drives in a row fail... but I know that is unusual!

[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)

You followed this link exactly to create the array?

As asked before, what does the mdadm.conf file show?

---

### Post by joshlos on 2009-07-09
I must have very bad luck, it appears that sdf has gone bad. I ran a live CD and I'm getting all sorts of crazy errors on the drive. I'm currently doing a dd if=/dev/urandom of=/dev/sdf to see if I can salvage the drive. I'll fdisk afterwords and start over.

How do I know for sure if the drive is dead? I'll be very disappointed because all four of these drives are new..

---

### Post by fjgaude on 2009-07-09
Dead drive, if it will not format then it is bad... send back under warrenty.

Now just one bad drive in an array of four should permit the array to assemble... you likely have other issues too.

---

