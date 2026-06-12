---
title: "mdadm woes"
date: 2009-08-23
forum: Server Platforms
---

### Post by datarhythm on 2009-08-23
So very strange issue. One day, I find that my /dev/md0 isn't started, as you can see here:

```
root@server:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Thu Aug  7 20:53:43 2008
     Raid Level : raid5
  Used Dev Size : 0
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Aug 23 01:50:00 2009
          State : clean, Not Started
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 68a10b2d:87c6a90a:01f9e43d:ac30fbff (local to host server)
         Events : 0.1973050

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       64        3      active sync   /dev/sde
       4       8       96        4      active sync   /dev/sdg
       5       8      112        5      active sync   /dev/sdh

```

When I try to start it, it says it's busy:

```
root@server:~# mdadm --manage -R /dev/md0
mdadm: failed to run array /dev/md0: Device or resource busy
```

So I try stopping it and starting it again.
```
root@server:~# mdadm --manage -S /dev/md0
mdadm: stopped /dev/md0
root@server:~# mdadm --manage -R /dev/md0
mdadm: failed to run array /dev/md0: Invalid argument
```

Scratching my head, I try 'rebuilding' it.
```
root@server:~# mdadm --manage -S /dev/md0
mdadm: stopped /dev/md0
root@server:~# mdadm --assemble -R /dev/md0
mdadm: /dev/md0 has been started with 6 drives and 1 spare.

```

I suddenly realize, hey, I should have 7 disks, not 6. My hotspare was missing from my original output. I try looking at the details again to see if anything changed.

```
root@server:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Thu Aug  7 20:53:43 2008
     Raid Level : raid5
  Used Dev Size : 0
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Aug 23 01:59:28 2009
          State : clean, Not Started
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 68a10b2d:87c6a90a:01f9e43d:ac30fbff (local to host server)
         Events : 0.1973052

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       64        3      active sync   /dev/sde
       4       8       96        4      active sync   /dev/sdg
       5       8      112        5      active sync   /dev/sdh

```

That's a negative. Then I try adding it manually:

```
root@server:~# mdadm --manage -a /dev/md0 /dev/sdf
mdadm: add new device failed for /dev/sdf as 6: No space left on device
```

So then I try approaching it differently.

```
root@server:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdb1[0] sdh[5] sdg[4] sde[3] sdd1[2] sdc1[1]
      **0 blocks** level 5, 64k chunk, algorithm 2 [6/6] [UUUUUU]

unused devices: <none>
```

Zero blocks?!?!

Please don't tell me I just lost everything...

Please help!!!

---

### Post by datarhythm on 2009-08-23
Another interesting thing I found:

```
root@server:~# mdadm --examine /dev/md0
mdadm: No md superblock detected on /dev/md0.
```

This isn't looking good.

---

### Post by datarhythm on 2009-08-23
Getting closer to the issue... maybe:

```
root@server:~# mdadm -E /dev/sdf
/dev/sdf:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 68a10b2d:87c6a90a:01f9e43d:ac30fbff (local to host server)
  Creation Time : Thu Aug  7 20:53:43 2008
     Raid Level : raid5
  Used Dev Size : 0
     Array Size : 0
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Sun Aug 23 02:27:14 2009
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0
       Checksum : db27b395 - correct
         Events : 1973064

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     6       8       80       -1      spare   /dev/sdf

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       64        3      active sync   /dev/sde
   4     4       8       96        4      active sync   /dev/sdg
   5     5       8      112        5      active sync   /dev/sdh

```

Something is missing somewhere. Anyone else have any ideas?

---

### Post by dk06 on 2009-08-23
[http://en.wikipedia.org/wiki/Mdadm](http://en.wikipedia.org/wiki/Mdadm)
> 
A common error when creating RAID devices is that the dmraid-driver has taken control of all the devices that are to be used in the new RAID device. Error-messages like this will occur:
 mdadm: Cannot open /dev/sdb1: Device or resource busy
 To solve this problem, you need to build a new initrd without the dmraid-driver. The following command does this on a system with the "2.6.18-8.1.6.el5"-kernel:
 mkinitrd --omit-dmraid /boot/NO_DMRAID_initrd-2.6.18-8.1.6.el5.img 2.6.18-8.1.6.el5
After this, the system has to be rebooted with the new initrd. Edit your /boot/grub/grub.conf to achieve this.
 Alternatively if you have a self customized and compiled kernel from a distro like Gentoo (the default option in gentoo) which doesn't use initrd then check kernel .conf file in /usr/src/linux for the line
 # CONFIG_BLK_DEV_DM is not configured
If the above line is set as follows:
 CONFIG_BLK_DEV_DM=yes
then You might have to disable that option, recompile the kernel, put it in /boot and finally edit grub conf file in /boot/grub. PLEASE be careful NOT to disable
 CONFIG_BLK_DEV_MD=yes
(Note the MD instead of DM) which is essential for raid to work at all!
 If both methods have not helped you then booting from live CD probably will (the below example is for starting a degraded raid-1 mirror array and adding a spare hdd to it and syncing. Creating a new one shouldn't be more difficult cause the underlying problem was 'Device or resource busy' error):
 modprobe raid1
mknod /dev/md1 b 9 1
mknod /dev/md3 b 9 3
mdadm --assemble /dev/md1 /dev/hda1
mdadm --assemble /dev/md3 /dev/hda1
mdadm --add /dev/md1 /dev/hdb1
mdadm --add /dev/md3 /dev/hdb3
Remember to change the corresponding md* and hd* values with the corresponding ones from your system. You can monitor the sync progress using:
 cat /proc/mdstat
When the sync is done you can reboot in your Linux normally.


This is just a common issue, not sure if it applies to your situation since you've already created it but I thought it was worth mentioning

---

### Post by datarhythm on 2009-08-23
Thanks for the reply. I tried it and here is what I got:

```
root@server:~# uname -a
Linux server 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
root@server:~# mkinitrd --omit-dmraid /boot/NO_DMRAID_initrd-2.6.18-11-generic 2.6.18-11-generic
-bash: mkinitrd: command not found

```

I'm not familiar with the mkinitrd command. Help?

---

### Post by datarhythm on 2009-08-23
So I tried shutting down and taking out the spare completely, but that didn't work (but it did change the 'spare' drive from sdf to sdh). 

After a lot of Googling, I found that some people were able to get their array back by mdadm -C it. It sound counter-intuitive (that it would initialize the array and destroy everything) but I took a leap of faith.

```
root@server:~# mdadm -C -l5 -n6 /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde /dev/sdf /dev/sdg -x1 /dev/sdh

mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid5 devices=6 ctime=Thu Aug  7 20:53:43 2008
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid5 devices=6 ctime=Thu Aug  7 20:53:43 2008
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid5 devices=6 ctime=Thu Aug  7 20:53:43 2008
mdadm: /dev/sde appears to be part of a raid array:
    level=raid5 devices=6 ctime=Thu Aug  7 20:53:43 2008
mdadm: /dev/sdf appears to be part of a raid array:
    level=raid5 devices=6 ctime=Thu Aug  7 20:53:43 2008
mdadm: /dev/sdg appears to be part of a raid array:
    level=raid5 devices=6 ctime=Thu Aug  7 20:53:43 2008
mdadm: /dev/sdh appears to be part of a raid array:
    level=raid5 devices=6 ctime=Thu Aug  7 20:53:43 2008
Continue creating array?

```
At this point, I'm thinking "this is probably going to be one of those moment in my life that I think back and say 'what the hell was I thinking?'" But I hit 'y' anyways.

```

mdadm: array /dev/md0 started.

```

And I checked it...

```

root@server:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sun Aug 23 10:37:55 2009
     Raid Level : raid5
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 6
  Total Devices : 7
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Aug 23 10:37:55 2009
          State : clean, degraded, recovering
 Active Devices : 5
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 2

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 0% complete

           UUID : 2eaf6765:d80e2c1b:01f9e43d:ac30fbff (local to host server)
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       64        3      active sync   /dev/sde
       4       8       80        4      active sync   /dev/sdf
       6       8       96        5      spare rebuilding   /dev/sdg

       7       8      112        -      spare   /dev/sdh

root@server:~# ls /dev/vgNAS/lvm0
/dev/vgNAS/lvm0


```

'No freaking way' I thought. 

```

root@server:~# mount /dev/vgNAS/lvm0 /mnt/NAS

root@server:~# df -h /mnt/NAS
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/vgNAS-lvm0
                      3.7T  3.0T  751G  80% /mnt/NAS


```

Sure enough, I poke around and see that my files are there... BUT some of it comes back as like this:

```

ls /mnt/NAS/M*
??????????  ? ?    ?             ?                ? Movies
??????????  ? ?    ?             ?                ? Music

```

Has anyone ran into this before? I can't access the files that are like this but some of the others are just fine. Should I just wait for the rebuilt process to finish?

```

root@server:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [ra                                    id10]
md0 : active raid5 sdg[6] sdh[7](S) sdf[4] sde[3] sdd1[2] sdc1[1] sdb1[0]
      4883799680 blocks level 5, 64k chunk, algorithm 2 [6/5] [UUUUU_]
      [>....................]  recovery =  0.5% (5573772/976759936) finish=250.8 min speed=64512K/sec

```


I know it shouldn't matter but, when I try to chown it, it says either 'cannot access' or 'Structure needs cleaning'.

I'll continue to Google but any help would be appreciated!

---

### Post by datarhythm on 2009-08-23
Looks like preliminary findings of Google points to an XFS issue. After array is 100% rebuilt, I'll try a xfs_check and xfs_repair.

Strange that this all happened randomly one day. I wonder what caused this. I'll keep everyone posted on what happens after I run the above commands.

---

### Post by datarhythm on 2009-08-24
No luck with the xfs_repair. I'm starting to think it's fried beyond repair but I've sent off an email to the XFS group with my findings.

Hopefully someone out there can help me before I throw up my hands and start all over.

---

### Post by tgrimley on 2009-08-24
subbed.

I can't offer any help but I appreciate your posting each step of the way and what you discover; it will hopefully be helpful to the next person. :)

---

### Post by datarhythm on 2009-08-24
No problem :-)

I don't know why I thought creating [this]("http://ubuntuforums.org/showthread.php?t=1248217&highlight=xfs_repair") in 'general help' would have been better, but this is the snippets from my nfs_repair output. 

FYI, I tried both the xfsprogs out in the repositories (v2 I think) and the latest and greatest (v3.0.1).

---

### Post by dk06 on 2009-08-24
> **datarhythm said:**
> No problem :-)

I don't know why I thought creating [this]("http://ubuntuforums.org/showthread.php?t=1248217&highlight=xfs_repair") in 'general help' would have been better, but this is the snippets from my nfs_repair output. 

FYI, I tried both the xfsprogs out in the repositories (v2 I think) and the latest and greatest (v3.0.1).

The guys over in the linux forums are pretty sharp when it comes to server/raid issues, maybe give them a shot:  [http://www.linuxforums.org/](http://www.linuxforums.org/)

& maybe post in Debian as well as Ubuntu, 
I think there are more Debian server admins in general than Ubuntu so they may be able to offer more help
Good Luck

---

### Post by datarhythm on 2009-08-24
OK. So I think I know what happened (to the XFS that is). 

Remember when I said:

"this is probably going to be one of those moments in my life that I think back and say 'what the hell was I thinking?'"

Well, I pretty sure I was spot on on my prediction. You see, when you build a RAID5 array, and you specify the order of the devices in which you build the array (/dev/sdb1, /dev/sdc1, etc), the ORDER is **_VERY IMPORTAN_**T. So when I had did mdadm -C (blah blah), I should have put the exact order in which my original output was. If you can scroll back on that specific command I submitted, you'll see that it wasn't in the correct order.

So it wasn't that XFS got corrupted, I had just re-arranged the bits around such that XFS said "WTF?"

Story of my life.

The moral of the story, kids: Copy down the order in which you create a RAID5 array. At least I'm pretty sure that's what happened.

Needless to say, my data is gone. I can't 'rearrange' again to the proper order--already too late. And I don't have $2,500 lying around to get it repaired.

---

### Post by tgrimley on 2009-08-24
> **datarhythm said:**
>  I should have put the exact order in which my original output was. If you can scroll back on that specific command I submitted, you'll see that it wasn't in the correct order.

Will just confirm this.  When you assemble it doesn't matter (there is a superblock that tells mdadm what order) but when you recreate it must be in the same order as you originally created the array.

see [http://osdir.com/ml/linux-raid/2009-06/msg00165.html](http://osdir.com/ml/linux-raid/2009-06/msg00165.html) for additional confirmation.  glad your data is safe. (will remember this for when my raid array dies)

---

