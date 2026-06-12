---
title: "Please help, my array is degraded"
date: 2008-08-06
forum: Server Platforms
---

### Post by seepage87 on 2008-08-06
I have no idea what happened, but I didn't receive an email telling me something went wrong (I have in the past), it was just telling me that my /mnt/ (where my array is mounted) was read only.  I did a quick mdadm -D and got this:

```
alex@tess:/$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sun Dec  9 17:13:20 2007
     Raid Level : raid5
     Array Size : 2441919680 (2328.80 GiB 2500.53 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Aug  6 14:41:45 2008
          State : clean, degraded
 Active Devices : 4
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 62637b60:43cdfd6a:1cc26ced:e8d9c0eb
         Events : 0.696334

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       49        1      active sync   /dev/sdd1
       2       0        0        2      removed
       3       0        0        3      removed
       4       8       33        4      active sync   /dev/sdc1
       5       8       65        5      active sync   /dev/sde1

       6       8       97        -      faulty spare   /dev/sdg1
       7       8       81        -      faulty spare   /dev/sdf1

```

When I run cat /proc/mdstat I get this:
```

alex@tess:/$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdg1[6](F) sdb1[0] sde1[5] sdc1[4] sdf1[7](F) sdd1[1]
      2441919680 blocks level 5, 64k chunk, algorithm 2 [6/4] [UU__UU]

```

I don't know what faulty spare means, but every drive was in the RAID5 before, with sdg1 and sdf1 as drives, not spares.  Is there any hope of me recovering my data?

---

### Post by seepage87 on 2008-08-06
Also, I would like to at least make a backup of all the filenames with their full path, which I can still read.  How would I dump the whole folder tree into a text document or something?

---

### Post by y@w on 2008-08-06
It looks like you should be able to pull your data off.. I'm not sure what you're going to accomplish by dumping a list, but you can do 'ls -r /mnt/<mount_point> > file_list'. 

Can you still get to your data? If so, you'll need to copy that off to another drive or something asap.. It says that the RAID is degraded, not failed. It should be *ok*. You'll just need to replace the failed drive and rebuild the array.

---

### Post by quonsar on 2008-08-06
If He actually shows up, you won't be needing a RAID array anyhow.

---

### Post by y@w on 2008-08-06
> **quonsar said:**
> If He actually shows up, you won't be needing a RAID array anyhow.

Haha fair enough.

---

### Post by seepage87 on 2008-08-06
Well, that's just the thing.  It says degraded, but there are 2 drives that are labeled as a "faulty spare" in a RAID5, so I'm not yet convinced I can get my data off, or at least I don't know how to do it.  I tried to copy a file from my array to another drive and got:
```

cp: reading `/mnt/shared/Music/Sorted/BT/Emotional Technology/BT-Emotional Technology-04-Somnambulist (Simply Being Loved).mp3': Input/output error

```
So that doesn't seem to have worked.  The reason I want that dump is so at least I have a comprehensive list of what I've lost if I can't recover it.

A drive got "removed" once before, but I opened up my server and tightened everything and made sure it was ok and I just had to add the disk the the array, but it completely rebuilt that drive (took about 6 hours).  I'm worried that the same happened with both these drives, because I don't think it will know how to add them back in without rebuilding them.  In principal their blocks should be the same as before they messed up; I don't think the harddrives actually failed.  I feel like mdadm should be able to properly slip these drives back in without incident, but I'm scared to touch anything.  Any help???

---

### Post by quad3d@work on 2008-08-06
You are only allow "one" faulty/removed disk from a RAID5 array. You have "two"... what a draw of luck...


AFAIK, there is not a way to recover this type of error. I'm pretty sure you cannot rebuild the array by replacing sdg1 and sdf1. You are seeing some filenames is probably from the inode metadata.

I've experienced one disk failure, replaced the disk.... during the array rebuild second disk fails. Yes, it sucks.

---

### Post by seepage87 on 2008-08-06
Well, I know I can't have two disks fail.  But I seriously doubt there is anything wrong with the disks.  If you simply disconnect two drives, I'm pretty sure you can reconnect them and re-assemble since none of the blocks have changed, which is what I'm hoping to be able to do. I'm just not sure if there are any tricks I need to know to get it to do this right.

---

### Post by y@w on 2008-08-06
I guess I don't work with software RAIDs very often.. Why would it show "clean, degraded" as the state when it's not clean? If the RAID has failed, it can't be showing "clean". There seems to be something very fishy about this. Could it be that you just have a bad controller? This is why I don't use software RAIDs..

---

### Post by seepage87 on 2008-08-06
My guess is something messed up on the south bridge, not sure.  You'll notice that it also says the superblock is persistent and some other things which are promising.  It also doesn't say the drives are "failed", they're just labeled as removed, and somehow they got added as faulty spares.  Anyway, with all these things, I have some hope, I just need some help.

---

### Post by fjgaude on 2008-08-07
In your position I would stop and unmount the array then try a forced assemble, like so:

```
sudo mdadm --assemble -f --scan
```

and see what happens...

---

### Post by seepage87 on 2008-08-07
No luck :(  When I do that it gives:

```

alex@tess:~$ sudo mdadm --assemble -f --scan
mdadm: forcing event count in /dev/sdg1(3) from 696325 upto 696342
mdadm: clearing FAULTY flag for device 0 in /dev/md0 for /dev/sdg1
mdadm: /dev/md0 has been started with 5 drives (out of 6).

```
Which sounds promising, but mdadm -D gives:
```

alex@tess:/$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sun Dec  9 17:13:20 2007
     Raid Level : raid5
     Array Size : 2441919680 (2328.80 GiB 2500.53 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 6
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Aug  7 11:41:05 2008
          State : clean, degraded
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 62637b60:43cdfd6a:1cc26ced:e8d9c0eb
         Events : 0.696350

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       49        1      active sync   /dev/sdd1
       2       0        0        2      removed
       3       0        0        3      removed
       4       8       33        4      active sync   /dev/sdc1
       5       8       65        5      active sync   /dev/sde1

       6       8       97        -      faulty spare   /dev/sdg1


```
Which is worse than before, I guess.  I tried addeing /dev/sdf1 to the array but it just got tacked on as a spare.  I think I'm screwed, though if anyone has any other ideas, I'd love to hear them.

Assuming for a minute that I'm screwed, I'm going to want to rebuild my array (probably RAID6 this time).  But I don't what this to happen again, so first I need a good method to check my hard drives for all kinds of errors.  Then I need some ideas on why maybe the south bridge messed up (I still think that's what it was).  Do I maybe need better cooling (I have 3 stock fans) or a better power supply (I think I have 500W)?  Thanks.

---

### Post by fjgaude on 2008-08-07
Gosh, it'll very difficult to tell why hardware goes bad, faults.

It would seem that by understanding everything you did and why you can figure out what and why this happened.

Three things to read, study:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
   then **/usr/share/doc/mdadm/FAQ.g**z  and **md.txt.gz**
[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

One last thing to try: delete the **/etc/mdadm/mdadm.conf** and **mdadm**. Reboot, install mdadm then run:

```
sudo --assemble --scan
```

You will now have a new up-to-date mdadm.conf file and things may be okay. See if you can copy important data to a backup drive.

---

### Post by seepage87 on 2008-08-08
Thanks, but no luck:
```

alex@tess:~$ sudo mdadm --assemble --scan
mdadm: /dev/md0 assembled from 4 drives and 2 spares - not enough to start the array.

```

I'm starting to lose hope.  At least much of it can be reacquired.  What's the best way to check the disks for errors to make sure they aren't the problem?

---

### Post by quad3d@work on 2008-08-08
> **seepage87 said:**
> Thanks, but no luck:
I'm starting to lose hope.  At least much of it can be reacquired.  What's the best way to check the disks for errors to make sure they aren't the problem?

You can check out smartmontools. Recently I had couple drives kicking out I/O errors but smartmontools said drives were good... I'm sure in Windows world there are better tools.

---

