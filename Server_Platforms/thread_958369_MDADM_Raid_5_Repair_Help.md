---
title: "MDADM Raid 5 Repair Help"
date: 2008-10-25
forum: Server Platforms
---

### Post by santhony on 2008-10-25
My Raid 5 has failed due to a Power Supply issue. I'm unable to repair or assemble my array. I haven't tried much in fear of damaging my set further.

My normal procedures for restarting my Array is not working:

santhony@ubuntu:~$ sudo mdadm --detail /dev/md0
[sudo] password for santhony:
mdadm: metadata format 00.90 unknown, ignored.
mdadm: md device /dev/md0 does not appear to be active.
santhony@ubuntu:~$

santhony@ubuntu:~$ sudo mdadm --assemble --scan
mdadm: metadata format 00.90 unknown, ignored.
mdadm: /dev/md0 assembled from 2 drives and 1 spare - not enough to start the array.
santhony@ubuntu:~$

santhony@ubuntu:~$ sudo mdadm --assemble --verbose /dev/md0 /dev/sdb1 /dev/sdf1 /dev/sdd1 /dev/sde1 /dev/sda1
mdadm: metadata format 00.90 unknown, ignored.
mdadm: looking for devices for /dev/md0
mdadm: no RAID superblock on /dev/sda1
mdadm: /dev/sda1 has no superblock - assembly aborted

Please advise on what I should do to reassemble.

---

### Post by santhony on 2008-10-25
More Info:

Now for exaimine, I get similiar output for all drives except sda1.

santhony@ubuntu:~$ sudo mdadm --examine /dev/sda1
mdadm: metadata format 00.90 unknown, ignored.
mdadm: No md superblock detected on /dev/sda1.

I receive similar output of this from drives SDB1, SDD1, SDE1 and SDF1:

santhony@ubuntu:~$ sudo mdadm --examine /dev/sdb1
mdadm: metadata format 00.90 unknown, ignored.
/dev/sdb1:
Magic : a92b4efc
Version : 00.90.00
UUID : 67350c39:89f0ac91:0f5b4e61:2c17f314
Creation Time : Mon Jul 14 15:01:56 2008
Raid Level : raid5
Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
Array Size : 1953535744 (1863.04 GiB 2000.42 GB)
Raid Devices : 5
Total Devices : 5
Preferred Minor : 0

Update Time : Thu Oct 23 01:01:51 2008
State : clean
Active Devices : 4
Working Devices : 5
Failed Devices : 1
Spare Devices : 1
Checksum : 8473b682 - correct
Events : 741092

Layout : left-symmetric
Chunk Size : 64K

Number Major Minor RaidDevice State
this 4 8 17 4 active sync /dev/sdb1

0 0 8 49 0 active sync /dev/sdd1
1 1 8 1 1 active sync
2 2 8 65 2 active sync /dev/sde1
3 3 0 0 3 faulty removed
4 4 8 17 4 active sync /dev/sdb1
5 5 8 81 5 spare /dev/sdf1



PLEASE HELP...
santhony is online now Report Post   	Edit/Delete Message

---

### Post by fjgaude on 2008-10-25
Gosh, seems like you have at least two of your five drives failed... the only thing I can think of is to try a --force assemble.

```
sudo mdadm --assemble --scan -f
```

and see it that works.

Your array could have handled one drive failure but not two, it's raid5. You could have had one failed without your knowledge then when the next one failed your array is toast.

Let us know how things go.

---

### Post by santhony on 2008-10-25
Just tried the force...

santhony@ubuntu:~$ sudo mdadm --assemble --scan -f
mdadm: metadata format 00.90 unknown, ignored.
mdadm: forcing event count in /dev/sdb1(4) from 741092 upto 741106
Segmentation fault
santhony@ubuntu:~$ 


I hate to think this is toast.. I've had this data set for nearly 10 years.  I've run it on Windows 2k and moved it over to mdadm the past year...

All of the drives are still good, I didn't suffer any real hard drives failure..  The Power supply went and couldn't handle enough power to the drives.  

If I do an eximine on the drives, it does show they are set for a Raid 5..

---

### Post by santhony on 2008-10-25
If I try and rebuild without drive sda1, it goes a bit further..

santhony@ubuntu:~$ sudo mdadm --assemble --verbose /dev/md0 /dev/sdf1 /dev/sdb1 /dev/sdd1 /dev/sde1
[sudo] password for santhony: 
mdadm: metadata format 00.90 unknown, ignored.
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 5.
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 4.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 2.
mdadm: no uptodate device for slot 1 of /dev/md0
mdadm: added /dev/sde1 to /dev/md0 as 2
mdadm: no uptodate device for slot 3 of /dev/md0
mdadm: added /dev/sdb1 to /dev/md0 as 4
mdadm: added /dev/sdf1 to /dev/md0 as 5
mdadm: added /dev/sdd1 to /dev/md0 as 0
mdadm: /dev/md0 assembled from 2 drives and 1 spare - not enough to start the array.
santhony@ubuntu:~$ sudo cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] 
md0 : inactive sdd1[0](S) sdf1[5](S) sdb1[4](S) sde1[2](S)
      1953535744 blocks
       
unused devices: <none>


How come it doesn't try and use all the drives.. It's only looking at 3 drives as part of the array??

---

### Post by santhony on 2008-10-25
It Looks Like I may have it a Bug... 

I feel Like I hit every known Bug to Linux....

[http://www.nabble.com/Bug-499643:-Segmentation-fault-when-attempting-re-assembly-of-a-failed-RAID5-via-%22mdadm--v--A---run---force%22-td19589839.html](http://www.nabble.com/Bug-499643:-Segmentation-fault-when-attempting-re-assembly-of-a-failed-RAID5-via-%22mdadm--v--A---run---force%22-td19589839.html)

The system is a clean 1-day old installation of Lenny.
Doing tests of RAID re-assembly, by failing devices and having mdadm rebuild
them. Had manually failed 2 devices on a 5-drive RAID5, causing it to stop.
All attempts at forced re-assembly ended with SegFault, e.g.

# mdadm -v -A --force --run /dev/md0 /dev/loop[0-4]
mdadm: looking for devices for /dev/md0
mdadm: /dev/loop0 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/loop1 is identified as a member of /dev/md0, slot 5.
mdadm: /dev/loop2 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/loop3 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/loop4 is identified as a member of /dev/md0, slot 1.
mdadm: forcing event count in /dev/loop4(1) from 74 upto 80
Segmentation fault

After many retries and failures, I downloaded older version of
mdadm v2.6.4 from neilb's site and compiled it and it worked fine
(no segfault):

# ./mdadm -v -A --run --force /dev/md0 /dev/loop0 /dev/loop2 /dev/loop3 /dev/loo
p4 /dev/loop1
mdadm: looking for devices for /dev/md0
mdadm: /dev/loop0 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/loop2 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/loop3 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/loop4 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/loop1 is identified as a member of /dev/md0, slot 5.
mdadm: forcing event count in /dev/loop4(1) from 74 upto 80
mdadm: clearing FAULTY flag for device 3 in /dev/md0 for /dev/loop4
mdadm: added /dev/loop4 to /dev/md0 as 1
mdadm: added /dev/loop2 to /dev/md0 as 2
mdadm: added /dev/loop3 to /dev/md0 as 3
mdadm: no uptodate device for slot 4 of /dev/md0
mdadm: added /dev/loop1 to /dev/md0 as 5
mdadm: added /dev/loop0 to /dev/md0 as 0
mdadm: /dev/md0 has been started with 4 drives (out of 5) and 1 spare.

---

### Post by fjgaude on 2008-10-25
Wow, never have seen this before. You are saying that version 2.6.4 of mdadm works and 2.6.7 doesn't?

Ubuntu 8.10RC includes 2.6.7... wonder what the bug is and how it will be fixed?

Let us know if the older version works for you, please.

Just checked the mdadm 2.6.7 and it is dated June '08. So it has been out that long and nobody has noted this bug!

---

### Post by santhony on 2008-10-25
Yes, I have downgraded to mdadm 2.6.3 and I was now able to force the build.

My Raid set is now recovering!!!

santhony@ubuntu:~$ sudo mdadm --detail /dev/md0
[sudo] password for santhony: 
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90.03
  Creation Time : Mon Jul 14 15:01:56 2008
     Raid Level : raid5
     Array Size : 1953535744 (1863.04 GiB 2000.42 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Oct 25 12:25:50 2008
          State : clean, degraded, recovering
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 1% complete

           UUID : 67350c39:89f0ac91:0f5b4e61:2c17f314
         Events : 0.741110

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8        1        1      active sync   /dev/sda1
       2       8       65        2      active sync   /dev/sde1
       5       8       81        3      spare rebuilding   /dev/sdf1
       4       8       17        4      active sync   /dev/sdb1
santhony@ubuntu:~$ 


santhony@ubuntu:~$ sudo cat /proc/mdstat  
Personalities : [raid6] [raid5] [raid4] 
md0 : active raid5 sdd1[0] sdf1[5] sdb1[4] sde1[2] sda1[1]
      1953535744 blocks level 5, 64k chunk, algorithm 2 [5/4] [UUU_U]
      [>....................]  recovery =  4.7% (23388104/488383936) finish=236.2min speed=32805K/sec
      
unused devices: <none>
santhony@ubuntu:~$

---

### Post by fjgaude on 2008-10-25
Wonderful... now, speaking of **backups**. <smile>

Are you up to filing a bug report?

As an aside, the watch command is useful showing the building of an array:

```
sudo watch cat /proc/mdstat
```

Thought you might not know this.

---

### Post by santhony on 2008-10-25
Thanks Frank..

I actually had posted the watch /cat/proc/mdstat in my last reply..haha

I found this bug listed from the URL in my previous post also, so I take it that it's been reported already.

Bug#499643: Segmentation fault when attempting re-assembly of a failed RAID5 via "mdadm -v -A --run --force"

[http://www.nabble.com/Bug-499643:-Segmentation-fault-when-attempting-re-assembly-of-a-failed-RAID5-via-%22mdadm--v--A---run---force%22-td19589839.html](http://www.nabble.com/Bug-499643:-Segmentation-fault-when-attempting-re-assembly-of-a-failed-RAID5-via-%22mdadm--v--A---run---force%22-td19589839.html)

---

### Post by fjgaude on 2008-10-25
Thanks again, I'm not reading too clearly right now. <smile>

---

### Post by 241comp on 2008-11-13
I recently had my software raid 5 array fail and was getting segfaults when trying to force a reassembly.  Per the suggestion in this thread, I downgraded to mdadm 2.6.4 and my array is now rebuilding.  So, just chiming in to say it works and THANK YOU for posting your resolution rather than just finding the fix and not posting back.

---

