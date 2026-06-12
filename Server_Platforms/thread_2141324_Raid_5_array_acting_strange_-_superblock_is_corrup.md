---
title: "Raid 5 array acting strange - superblock is corrupt, and disk is maybe faulty"
date: 2013-05-02
forum: Server Platforms
---

### Post by runlifttrimswole on 2013-05-02
Hey everyone, I've been hacking at this on and off for a couple days and am clearly in a little over my head.  :(  

I set up a raid 5 with 3 disks a few years ago and have had no problems until we had a power outage last week.   I rebooted and md0 wouldn't come online.  I didn't save the error message, but it said the superblock was bad.  I did some research and decided to force assembly. 

```
mdadm --assemble -f /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1
```

Now I'm not sure what's going on, but after I can't mount the device:

```
mount -t jfs /dev/md0 /media/atropos/
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
fsck is not encouraging:
```
$ sudo fsck /dev/md0

fsck 1.41.4 (27-Jan-2009)
fsck.jfs version 1.1.12, 24-Aug-2007
processing started: 5/2/2013 6.48.58
Using default parameter: -p
The current device is:  /dev/md0
ujfs_rw_diskblocks: read 0 of 4096 bytes at offset 32768
ujfs_rw_diskblocks: read 0 of 4096 bytes at offset 61440
Superblock is corrupt and cannot be repaired
since both primary and secondary copies are corrupt.

```

Here is some other relevant info:


```
$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[1] sdb1[3](S) sdd1[4](F)
      2930271744 blocks level 5, 128k chunk, algorithm 2 [3/1] [_U_]

```


So sdd1 is failing for some reason, right?   If you examine each drive independently they have different ideas about what's going on with the raid.  sdb1 doesn't even see sdd1 in the array, sdc thinks we're in trouble, and sdd thinks everything is great. Meanwhile, there's no superblock on md0:



```
$ sudo mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : da23b88a:4d0610cf:b45df8ba:2efcec8c (local to host atropos)
  Creation Time : Sat Sep 26 21:57:56 2009
     Raid Level : raid5
  Used Dev Size : 1465135872 (1397.26 GiB 1500.30 GB)
     Array Size : 2930271744 (2794.52 GiB 3000.60 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0


    Update Time : Thu May  2 06:10:19 2013
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1
       Checksum : a747a350 - correct
         Events : 3448


         Layout : left-symmetric
     Chunk Size : 128K


      Number   Major   Minor   RaidDevice State
this     3       8       17        3      spare   /dev/sdb1


   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed
   3     3       8       17        3      spare   /dev/sdb1


$ sudo mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : da23b88a:4d0610cf:b45df8ba:2efcec8c (local to host atropos)
  Creation Time : Sat Sep 26 21:57:56 2009
     Raid Level : raid5
  Used Dev Size : 1465135872 (1397.26 GiB 1500.30 GB)
     Array Size : 2930271744 (2794.52 GiB 3000.60 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0


    Update Time : Thu May  2 06:10:19 2013
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1
       Checksum : a747a362 - correct
         Events : 3448


         Layout : left-symmetric
     Chunk Size : 128K


      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1


   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed
   3     3       8       17        3      spare   /dev/sdb1

$ sudo mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : da23b88a:4d0610cf:b45df8ba:2efcec8c (local to host atropos)
  Creation Time : Sat Sep 26 21:57:56 2009
     Raid Level : raid5
  Used Dev Size : 1465135872 (1397.26 GiB 1500.30 GB)
     Array Size : 2930271744 (2794.52 GiB 3000.60 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0


    Update Time : Wed May  1 21:27:27 2013
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1
       Checksum : a74728cd - correct
         Events : 3440


         Layout : left-symmetric
     Chunk Size : 128K


      Number   Major   Minor   RaidDevice State
this     2       8       49        2      active sync   /dev/sdd1


   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       17        3      spare   /dev/sdb1




$ sudo mdadm --examine /dev/md0
mdadm: No md superblock detected on /dev/md0.






```


Help?  I was thinking about removing sdd from the array and shoving it back in, but that terrifies me :(

---

### Post by darkod on 2013-05-02
How about if you try something like:
```
sudo mdadm --assemble --verbose --force --run --metadata=0.90 /dev/md0 /dev/sd[bcd]1
```

See if that can help.

---

### Post by runlifttrimswole on 2013-05-02
wow, thanks for the quick response!

```
$sudo mdadm --assemble --verbose --force --run --metadata=0.90 /dev/md0 /dev/sd[bcd]1
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 2.
mdadm: forcing event count in /dev/sdd1(2) from 3440 upto 3448
mdadm: clearing FAULTY flag for device 2 in /dev/md0 for /dev/sdd1
mdadm: no uptodate device for slot 0 of /dev/md0
mdadm: added /dev/sdd1 to /dev/md0 as 2
mdadm: added /dev/sdb1 to /dev/md0 as 3
mdadm: added /dev/sdc1 to /dev/md0 as 1
mdadm: /dev/md0 has been started with 2 drives (out of 3) and 1 spare.

$sudo mdadm --examine /dev/md0
mdadm: No md superblock detected on /dev/md0.

$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[1] sdb1[3] sdd1[2]
      2930271744 blocks level 5, 128k chunk, algorithm 2 [3/2] [_UU]
      [>....................]  recovery =  0.2% (3253104/1465135872) finish=539.7min speed=45137K/sec


unused devices: <none>






```

Do I need to wait for it to recover and see what happens?  Still no superblock is scary, right?  It looks like --metadata=0.90 just forced a "standard" superblock onto the system, yes?

---

### Post by darkod on 2013-05-02
First, you don't run --examine on the md devices. So the message you receive is not a problem. You run --examine on the members, not the array. You can run --detail on the array.

Yes, wait for the sync to finish, I think at the end it will convert the spare to active member.

Since you can see from your --examine result that the metadata version is 0.90 (the latest is 1.2) because you have this array since years ago, I added that option to specify the metadata version. I wasn't sure it's needed, but it can't hurt.

I'm not sure if that helped, or adding also the --run option, but among them it seems something worked.

You can try mounting md0 while the sync is going on. Since this is raid5 array that can work without one member, it should be able to mount. It's up to you if you want to wait for the sync to finish first.

Again, the --examine /dev/md0 is not a problem, don't worry about it. You're not supposed to run it on md0.

---

### Post by runlifttrimswole on 2013-05-02
Things looked good in the start

```
 $ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdd1[2] sdc1[1] sdb1[3]
      2930271744 blocks level 5, 128k chunk, algorithm 2 [3/2] [_UU]
      [=============>.......]  recovery = 68.4% (1003054456/1465135872) finish=153.0min speed=50302K/sec



```

but after it was done recovering it still says sdd1 is a failure:

```
 $ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdd1[3](F) sdc1[1] sdb1[4](S)
      2930271744 blocks level 5, 128k chunk, algorithm 2 [3/1] [_U_]


unused devices: <none>



```


Do I have a bad drive? What's my next step? 

Thanks!

---

### Post by darkod on 2013-05-03
Unfortunately it looks like sdd has gone bad. The problem is that sdb is also not a full member of the array so at the moment you are missing two members which raid5 can't handle. You haven't changed any of the disks yet, right? They are the same as before?

I can understand if sdd failed but why would sdb be marked as spare too? If it was always a member of the array, it should be an active member.

What if you try to assemble it from sdb and sdc only?
```
sudo mdadm --stop /dev/md0
sudo mdadm --verbose --assemble --metadata=0.90 /dev/md0 /dev/sd[bc]1
```

In the second command I deliberately didn't put --force and --run, try it like that first and if it doesn't work try it with --force.

---

### Post by runlifttrimswole on 2013-05-03
Well this is weird...  Note i've always only had these three drives in the array.

```
sudo mdadm --verbose --assemble --metadata=0.90 /dev/md0 /dev/sd[bc]1
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 4.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 1.
mdadm: no uptodate device for slot 0 of /dev/md0
mdadm: no uptodate device for slot 2 of /dev/md0
mdadm: added /dev/sdb1 to /dev/md0 as 4
mdadm: added /dev/sdc1 to /dev/md0 as 1
mdadm: /dev/md0 assembled from 1 drive and 1 spare - not enough to start the array.



```

---

### Post by darkod on 2013-05-03
And it moved sdb1 one slot further. Earlier when you ran the --assemble it said sdb1 member at slot 3, now it says 4.

What could have happened is that sdb1 was dropped long ago, and then marked as spare only. The array kept going without you noticing since it can work with one member missing. But when sdd1 failed, it's over. This is just a speculation, what could have happened.

Any chance you have a spare disk laying around or you could borrow one? You could make a sector by sector copy of sdd and see if you can assemble the array from sdc and sdd successfully. After that you would add sdb which will again be marked as spare at start, and it will begin syncing. Once the sync is gone, it should be active member and you could remove the borrowed/temp disk or replace it immediately with a new one.

Unfortunately, at this moment you seem pretty much scre*ed with one disk failing and the other not having all data on it (not a full active member).

PS. In fact, one option is to dd copy sdd to sdb. Since sdb is not a full member and is only marked as spare, it's not helping assemble the array.
But if you do manage to copy sdd which should be a full member until it failed, onto sdb, and then assemble from sdb and sdc only, with 2 out of 3 disks it should start.

At that point, you can consider replacing sdd with a new disk right away, or giving it one shot more and zeroing the superblock (this is very important in order not to confuse the array) and try adding it like a new disk that was never in the array. Zeroing the superblock will delete all info that it was ever member of this array. Of course, don't zero the superblock before you dd copy sdd to sdb, do that first.

These are just my ideas, it's your decision what you like adn what you don't. :)

---

### Post by runlifttrimswole on 2013-05-03
Ok, that's what my suspicion was. :(

I'll pick the option that has has the highest chance of success.  Would that be picking up the same drive as sdd for $100 and using DD to copy everything to the new drive?
 
Just to be sure, that's just doing this right : ```
*dd if=/dev/sdd of=/dev/sdf*
```

What's like likelihood that that is going to work since SDD is damaged in some way? 

If sdd is not recoverable can I still get some of the data that was on sdc back?

Thanks again for your help.  I'll order the new drive today. Once I get it I just DD up above and then

```
sudo mdadm --verbose --assemble --metadata=0.90 /dev/md0 /dev/sd[cf]1
```

yes?

---

### Post by darkod on 2013-05-03
Actually for copying a failing disk, ddrescue seems like a better option. You also have to be careful since it seems there are multiple packages with similar name, for slightly different programs. According to this (especially the askubuntu link), you should install the gddrescue package in ubuntu and use the command as ddrescue:
```
sudo apt-get install gddrescue
```
Source: [http://askubuntu.com/questions/211578/whats-the-difference-between-ddrescue-gddrescue-and-dd-rescue](http://askubuntu.com/questions/211578/whats-the-difference-between-ddrescue-gddrescue-and-dd-rescue)

In this link there is Example 3 for copying whole disk:
[http://www.forensicswiki.org/wiki/Ddrescue](http://www.forensicswiki.org/wiki/Ddrescue)
The best procedure seems to be:
```
sudo ddrescue -n /dev/sdd /dev/sdf rescue.log
sudo ddrescue -r=3 /dev/sdd /dev/sdf rescue.log
```

Unless you delete sdb (I guess you meant sdb although you wrote sdc, sdc seems to be the only fully working disk, no need to try to get anything from it) you can alwaus try to get back some data from it too. But according to how mdadm reacted during the assemble, sdd is the best bet. Some data might be corrupted, but it says ddrescue will try to get most of it out including the corrupted sectors.

After that is done, I would try first to assemble only with sdc1 and sdf1, like you suggested in your last post too. If that starts the array with 2 members, I would zero the superblock of sdb1 and try to add it like a disk that was never in the array. Hopefully it will sync fully and become a full member finally.

---

