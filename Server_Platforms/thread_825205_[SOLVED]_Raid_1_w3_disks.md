---
title: "[SOLVED] Raid 1 w/3 disks"
date: 2008-06-10
forum: Server Platforms
---

### Post by ubrgeek on 2008-06-10
I'm 100 percent certain that this is answered somewhere, but I can't seem to figure out what search terms will help me find it. If someone knows the location, I'd appreciate a point in the right direction so I don't have to ask anyone to repeat something they've already posted.

I'm trying to set up a software RAID 1 solution with with Ubuntu server (v 8.04) using three disks.  I've read up on it [here]("http://mywheel.net/blog/index.php/software-raid-in-ubuntu") and [here]("http://bobbyallen.wordpress.com/2008/05/19/installing-ubuntu-with-a-software-raid1-configuration/") and I think I'll be OK with that part. But none of the things I've read talk about doing the setup with three disks. 

I'd like to use one drive (SATA) for the operating system and some applications (webmin, Jinzora, a document management system and maybe a wikki. This is all for intranet-access only so not overly concerned with locking it down.) I want to use two 750gb drives (SATA) for the raid drives.  Like I said, I think I'm (fairly) confident in being able to do the two drives, but only as part of a fresh install.  I'm not sure where to look for a guide on doing what I'm looking to do. Like I said, if someone can direct me to a tutorial, I'd really appreciate it.

---

### Post by inphektion on 2008-06-10
I think what you need to read up on is how RAID works as RAID 1 and 3 disks go together like oil and water.  RAID 1 implies an even number of discs (specifically 2) as they are mirror copies of each other.  There is a RAID 10 level which is basically a RAID 0 (multiples drives combined into looking like one) then mirrored (RAID 1) to another exact RAID 0 set.  

You could set two disks up as a RAID 1 and then use the 3rd as a hot spare which means if one disk fails the hot spare takes over immediatley and this way you don't run in degraded mode while you replace a disk.

For a fresh install I did this with 2 Seagate 500GB using 64 bit alternate install cd which allowed me to configure the software RAID 1 right from the start.

---

### Post by TheGameAh on 2008-06-11
I currently have a 3 disk RAID1 setup, and everything seems to be running fine.  Could you give me some tips on why this is not a good setup?

---

### Post by inphektion on 2008-06-11
Because it isn't possible.  You must have a 2 disk RAID 1 and then a third standalone disk.  Which means that third disk is not RAID protected.

---

### Post by TheGameAh on 2008-06-11
?  Strange.  Seems to be possible on my mdadm setup.

#mdadm --detail /dev/md1

/dev/md1:
        Version : 00.90.03
  Creation Time : Tue Jun  3 05:56:10 2008
     Raid Level : raid1
     Array Size : 9767424 (9.31 GiB 10.00 GB)
    Device Size : 9767424 (9.31 GiB 10.00 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Wed Jun 11 10:50:13 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

           UUID : 9069f163:d74e3983:1b97ff05:1dbe7fa3
         Events : 0.260

    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
       1       8       21        1      active sync   /dev/sdb5
       2       8       37        2      active sync   /dev/sdc5

---

### Post by ubrgeek on 2008-06-11
I understand the equal-number-of-disk for RAID: That's what I'm looking at. The third disk isn't RAID protected; It's simply for the OS and a small number of apps I'm installing. I care about RAID'ing the disks holding the data, not the third OS/App disk..

---

### Post by TheGameAh on 2008-06-11
If you're looking for all post install stuff:

Just install the OS as usual on the desired drive, ignoring your 2nd and 3rd drives.  You can set this up after the install.

After the install, and everything is hunky dorey, you can use the command MDADM to setup your RAID1 on the 2nd and 3rd drives.  Put a file system on your new array (example ext3).  Then edit /etc/fstab so it will mount on bootup (remember to give it a mount point).  

Very quick summary, but that's the basic idea.  MDADM is the real key here, where you'll be spending a bit of time.

---

### Post by ubrgeek on 2008-06-11
Thanks TheGameAh :) I'll spend some time in the man pages for MDADM and google around. I really appreciate the guidance.

---

### Post by inphektion on 2008-06-11
> **TheGameAh said:**
> ?  Strange.  Seems to be possible on my mdadm setup.

#mdadm --detail /dev/md1

/dev/md1:
        Version : 00.90.03
  Creation Time : Tue Jun  3 05:56:10 2008
     Raid Level : raid1
     Array Size : 9767424 (9.31 GiB 10.00 GB)
    Device Size : 9767424 (9.31 GiB 10.00 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Wed Jun 11 10:50:13 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0



I'd love for someone to explain wtf mdadm thinks it's doing...  
I'm from a hardware RAID world (emc, hitachi, clarion, etc) and 3 disk RAID1 just isn't possible.  Its like dividing by zero.  What is it mirroring?  Is it just grouping all 3 disks into one like a RAID 0 and then splitting it in half virtually and mirroring those two virtual halves which make up 1.5 disks? :confused: 

just... makes... no sense....:confused:

---

### Post by inphektion on 2008-06-11
and what's up with the disk size?  what are you mirroring 3 4GB flash drives?  no way you have 4gb disks unless they are from a decade ago.

---

### Post by TheGameAh on 2008-06-12
Ah.  MDADM doesn't mirror entire disks.  It mirrors partitions.  What you're seeing above is a 3disk RAID1 partition.

I guess it's possible in software RAID.  :)  I always believed (although I could be wrong), that it was just a 3 way mirror.  The data is the same across all three drives.

I used to run a 2 disk mirror with a hotspare.  Then I saw it suggested that instead of having a hotspare, and having to rebuild during a failure, to just make it a 3 disk array, and no rebuilding necessary.

---

### Post by inphektion on 2008-06-12
Interesting.  thanks for explaination... I'll have to try to find some reading about what mdadm does or can do. Software RAID is like bizarro world.

---

### Post by andguent on 2008-06-12
While sometimes challenging, Software raid is immensely powerful. You also get to know exactly how the raid is doing with just a simple 'cat /proc/mdstat'. After a drive failure, it can also be easier to recover from then cheapie/fake hardware raid.

For anyone looking for misc software raid documentation, try these:
[http://really.slacking.net/~modat7/howto/RAID-mdadm-Setup.txt](http://really.slacking.net/~modat7/howto/RAID-mdadm-Setup.txt)
[http://www.linuxsa.org.au/mailing-list/2003-07/1270.html](http://www.linuxsa.org.au/mailing-list/2003-07/1270.html)
[https://alioth.debian.org/projects/rootraiddoc/](https://alioth.debian.org/projects/rootraiddoc/)

---

