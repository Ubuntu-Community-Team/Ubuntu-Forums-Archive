---
title: "How to install boot loader into RAID 10 setup?"
date: 2010-10-03
forum: Server Platforms
---

### Post by neoideo on 2010-10-03
Hello,

i installed ubuntu server on a 4-hard disk system, i installed with the RAID 10 support that comes with 10.04 server optioon.
my raid swap is /dev/md0  and my  raid data partition is /dev/md1

hard drives are  /dev/sda /dev/sdb /dev/sdc /dev/sdd 

the instalation goes fine, from the 8TB im getting 4TB mirrored which is what i want, 
but the instalation setup goes up to the point where it asks me to install grub boot loader, There i choose the default option and it does a fatal error.

my main goal is just to make it bootable, any method is welcome.
this went beyond my RAID knowledge (more conceptual than technical), any help is welcome

---

### Post by neoideo on 2010-10-03
i made it work partially. The problem im having now is that the server is working slow for just executing commands like ls or simpli logging in...password takes like 7 seconds to be prompted after typing user name.

sda, sdb, sdc, sdd each one is 2TB total

what i did was this:

made a 48GB SWAP RAID10 ( sda, sdb, sde, sdd )
made a 40GB Linux Ext4 partition in sda, as a master partition "/"
the rest of sda was used to be part of the RAID10 DATA PARTITION (around 1.93TB)
on sdb, sdc, and sdd i didnt reserve 40GB for linux, i just used the remaining space to from the RAID 10 Data partition, (around 1.97 TB each one, different to sda which contributed with 1.93TB).

Eventualy made the RAID10 Data partition Ext4 to be mounted on "/home" (around 4TB TOTAL)

installed ubuntu... (instalation went much slower than normal..first simptom that something was going wrong)

i wonder if that difference of size with sda and the others ....could have made the syustem function slower??? anyoine have any clue? solution possible??

---

### Post by neoideo on 2010-10-04
i tried another way

RAID10 for "/"

ordinary 100MB Partition for "/boot"
ordinary 20MB partition for biosgrub

installed all without errors.

speeds now seem to be ok, ill post them

---

