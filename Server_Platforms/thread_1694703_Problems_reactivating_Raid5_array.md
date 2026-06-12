---
title: "Problems reactivating Raid5 array"
date: 2011-02-24
forum: Server Platforms
---

### Post by fnords on 2011-02-24
I cannot get my Raid5 array to resync the array after mdadm --re-add /dev/sdg (forgot to plug-in the power chord accidentaly)
the drive appears as a spare but only 1 drive is a spare /dev/sdm



sudo mdadm --query --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Sat Jan 22 23:51:04 2011
     Raid Level : raid5
     Array Size : 13674590720 (13041.11 GiB 14002.78 GB)
  Used Dev Size : 1953512960 (1863.02 GiB 2000.40 GB)
   Raid Devices : 8
  Total Devices : 9
    Persistence : Superblock is persistent

    Update Time : Fri Feb 25 01:32:26 2011
          State : clean, degraded
 Active Devices : 7
Working Devices : 9
 Failed Devices : 0
  Spare Devices : 2

         Layout : left-symmetric
     Chunk Size : 512K

           Name : fnordistus-server:1  (local to host fnordistus-server)
           UUID : ba093fac:07394eaf:17756e0f:3bfdcb2d
         Events : 154

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       48        2      active sync   /dev/sdd
       3       8       32        3      active sync   /dev/sdc
       4       8       64        4      active sync   /dev/sde
       5       8       80        5      active sync   /dev/sdf
       9       8      192        6      spare rebuilding   /dev/sdm
       8       8      112        7      active sync   /dev/sdh

       6       8       96        -      spare   /dev/sdg



>>>

Personalities : [raid6] [raid5] [raid4] 
md1 : active raid5 sda[0] sdg[6](S) sdh[8] sdm[9] sdf[5] sde[4] sdc[3] sdd[2] sdb[1]
      13674590720 blocks super 1.2 level 5, 512k chunk, algorithm 2 [8/7] [UUUUUU_U]


NOTE:
nothing is rebuilding on /dev/sdm because mdstat doesnt show any resync, and sdm is just a spare /sdg is the drive

---

### Post by Vegan on 2011-02-24
I hate software RAID for the above reasons.

Use the MB RAID or a card, not a software RAID

---

### Post by YesWeCan on 2011-02-24
How about stopping the array and then reassembling it?
mdadm --stop /dev/md1
mdadm --assemble --scan

[edit - another idea]
I'm not certain how mdadm works, but I imagine it calls a re-added member a spare. In a sense it is a spare because it will need to be resync'd. You already have a spare. So the question is how does mdadm decide which spare to use? Perhaps it isn't doing the sync because of this. Besides, how can it build a replacement sdg when sdg is present? Perhaps telling mdadm to remove the original spare will kick it into action with sdg.

---

### Post by fnords on 2011-02-24
> **Vegan said:**
> I hate software RAID for the above reasons.

Use the MB RAID or a card, not a software RAID

I dont need your advise here.
A Hardware Raid has its own flaws, e.g a controller failure or whatsoever.
and a 600 Dollar Controller for just a Family server is overkill! even the 3GHz Quadcore can handle the load of 10 users easy.

---

### Post by fnords on 2011-02-24
> **YesWeCan said:**
> How about stopping the array and then reassembling it?
mdadm --stop /dev/md1
mdadm --assemble --scan

[edit - another idea]
I'm not certain how mdadm works, but I imagine it calls a re-added member a spare. In a sense it is a spare because it will need to be resync'd. You already have a spare. So the question is how does mdadm decide which spare to use? Perhaps it isn't doing the sync because of this. Besides, how can it build a replacement sdg when sdg is present? Perhaps telling mdadm to remove the original spare will kick it into action with sdg.


i stopped the array but restarting doesnt start resync.

---

### Post by fnords on 2011-02-24
> **YesWeCan said:**
> How about stopping the array and then reassembling it?
mdadm --stop /dev/md1
mdadm --assemble --scan

[edit - another idea]
I'm not certain how mdadm works, but I imagine it calls a re-added member a spare. In a sense it is a spare because it will need to be resync'd. You already have a spare. So the question is how does mdadm decide which spare to use? Perhaps it isn't doing the sync because of this. Besides, how can it build a replacement sdg when sdg is present? Perhaps telling mdadm to remove the original spare will kick it into action with sdg.



Ok i marked the drive /dev/sdm as faulty and mdstat reports now resync ends in 1750m
so after the resync i could add the /sdm again as hotspare with mdadm --add
Thanks 
73

---

### Post by rubylaser on 2011-02-25
Sorry I'm so late to the party.  I couldn't agree more about not needing a hardware RAID card for a home server.  Once the re-sync is done, you will be able to add it back with mdadm --add.

---

### Post by YesWeCan on 2011-02-25
> **fnords said:**
> Ok i marked the drive /dev/sdm as faulty and mdstat reports now resync ends in 1750m
so after the resync i could add the /sdm again as hotspare with mdadm --add
Thanks 
73
Good to know. Sort of dumb though. I am gradually trying to figure out how mdadm actually works. The existing documentation is a little light, particularly with regard to how to deal with real-life issues.

---

### Post by rubylaser on 2011-02-25
The Linux Raid wiki has a lot of real life examples.  Have you looked at these two sections?
[https://raid.wiki.kernel.org/index.php/Tweaking,_tuning_and_troubleshooting]("https://raid.wiki.kernel.org/index.php/Tweaking,_tuning_and_troubleshooting")
[https://raid.wiki.kernel.org/index.php/Reconstruction]("https://raid.wiki.kernel.org/index.php/Reconstruction")

The best way to learn, is setup a virtual machine with a bunch of disks, and disconnect them write data, and add them back, etc.  Try to break it, and then fix the problem.  It's really a good way to learn how it works in a lab environment.

---

### Post by YesWeCan on 2011-02-25
Thanks. BTW the first link led to this: [https://raid.wiki.kernel.org/index.php/Autodetect](https://raid.wiki.kernel.org/index.php/Autodetect)

Hard to tell what info in how-to pages is current and what is not.

---

### Post by rubylaser on 2011-02-25
The first link worked for me when I just tried it.  But, the second part about knowing what's current / out of date can sometimes be hard to tell.  Luckily, the man page is pretty darn good for mdadm, and if you're unsure, Google or people here on the forum are happy to lead a hand :)

---

