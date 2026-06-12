---
title: "mdadm raid 5 capacity smaller than expected"
date: 2013-06-26
forum: Server Platforms
---

### Post by hozzaconners on 2013-06-26
[FONT=arial]Hi all,

I've just taken my first steps into setting up a raid using mdadm, but I'm only seeing a capacity of 4TB when I would expect to see 6TB.

My setup is:

My setup is
HP Proliant Microserver
Ubuntu 12.04 installed on SSD (sde)
4x 2TB drives (sda/b/c/d)

I've been working my way through the following pages/tutorials, which seem to be v comprehensive:

[http://ubuntuforums.org/showthread.php?t=2115483](http://ubuntuforums.org/showthread.php?t=2115483)
[http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm)

I've done:
[/FONT]
[FONT=arial]```
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1 --spare-devices=1 /dev/sdd1

```
and then added it to mdadm.conf

After a reboot it appears as md127 (which in itself I don't understand - can anyone explain this to me?)

And then

```
sudo mkfs.ext4 md127
```

But the drive is only coming up with a capacity of 4TB, when I would expect a size of 6TB.

The output of ```
sudo mdadm --detail /dev/md127
``` is

> /dev/md127:
        Version : 1.2
  Creation Time : Sun Jun 23 22:31:55 2013
     Raid Level : raid5
     Array Size : 3906763776 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 1953381888 (1862.89 GiB 2000.26 GB)
   Raid Devices : 3
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Wed Jun 26 20:20:46 2013
          State : clean 
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : servername:0  (local to host servername)
           UUID : 4d8b387d:40005583:623d7964:4f4a7a62
         Events : 19

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       4       8       33        2      active sync   /dev/sdc1

       3       8       49        -      spare   /dev/sdd1

Can anybody tell me where I'm going wrong please?

Thanks!
[/FONT]

---

### Post by cool110 on 2013-06-26
You've made sdd a hot spare so there's only 3 drives in the array. So  taking away the spare drive and parity data will leave only 4TB  available.

---

### Post by rubylaser on 2013-06-26
> **hozzaconners said:**
> [FONT=arial]Hi all,

I've just taken my first steps into setting up a raid using mdadm, but I'm only seeing a capacity of 4TB when I would expect to see 6TB.

My setup is:

My setup is
HP Proliant Microserver
Ubuntu 12.04 installed on SSD (sde)
4x 2TB drives (sda/b/c/d)

I've been working my way through the following pages/tutorials, which seem to be v comprehensive:

[http://ubuntuforums.org/showthread.php?t=2115483](http://ubuntuforums.org/showthread.php?t=2115483)
[http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm)

I've done:
[/FONT]
[FONT=arial]```
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1 --spare-devices=1 /dev/sdd1

```
and then added it to mdadm.conf

After a reboot it appears as md127 (which in itself I don't understand - can anyone explain this to me?)

And then

```
sudo mkfs.ext4 md127
```

But the drive is only coming up with a capacity of 4TB, when I would expect a size of 6TB.

The output of ```
sudo mdadm --detail /dev/md127
``` is



Can anybody tell me where I'm going wrong please?

Thanks!
[/FONT]

Hello, I'm Zack Reed, so I'm glad you tried my tutorial :)  You created a disk RAID5 + 1 spare.  RAID5 requires 1 disk for parity, so you are only going to get the equivalent of 2 disks worth of storage with this setup (in your case this is the 4TB of usable space).  Just tell me conceptually what you were trying to do?  For example, I wanted 6TB of usable space while surviving 1 failed disk, or I wanted to have the ability to survive 2 disk failures, and in that case I would suggest using RAID6 instead of RAID5 + spare.

Also, md devices show up as md127 if there is something strange in the mdadm.conf file.  Could you please post the output of this?
```

cat /etc/mdadm/mdadm.conf

```

Finally, what do you intend to store on this array?  For most home users, I've become convinced that SnapRAID is likely a better solution than mdadm is (and I LOVE mdadm :) ).

---

### Post by hozzaconners on 2013-06-26
Ah, I thought I needed to tell it what the parity drive was, but thinking about it that doesn't make sense!

Thanks cool110, much appreciated!

---

### Post by hozzaconners on 2013-06-26
Wow, a reply from the man himself, I'm honoured!!!

I was trying to load up the 4x drive bays with 2TB drives and make a raid so that if I lose 1 drive I don't lose the lot. Raid 5 made sense to me, but I assumed I needed to notionally name a drive as the parity drive...which as cool110 says is wrong!

Output of 

```

cat /etc/mdadm/mdadm.conf
```
is
> # mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Sun, 23 Jun 2013 21:19:09 +0100
# by mkconf $Id$
ARRAY /dev/md0 metadata=1.2 spares=1 name=servername:0 UUID=4d8b387d:40005583:623d7964:4f4a7a62

I haven't set up the e-mail notifications yet, could that be the cause of md127?

As for use, it's a combo of home "stuff" (photos/general files/video files etc), but also a sandpit for learning about websites/e-mail etc, so hosting a couple of VM's that I can play with and learn on. If I use snapraid do I have to include the SSD/OS drive, or can I get away with the 4 bays as detailed above? What advantages can there be over mdadm?!?!

Thanks Zack!

---

### Post by rubylaser on 2013-06-26
You are using the word "honored" pretty loosely :)  All you need to do to add that spare drive to the array is to grow it.
```

mdadm --grow /dev/md127 --raid-devices=4

```
You'll need to watch the array grow and expand the filesystem.  [This tutorial]("http://zackreed.me/articles/48-adding-an-extra-disk-to-an-mdadm-array") will walk you through the rest of the process.

When you finish up the end of that tutorial writing out your mdadm.conf file, I would edit it, and remove the name section (and device back to /dev/md0 if it's still showing as /dev/md127) .  It is not needed to assemble the array and can cause assembly confusion.  It wouldn't hurt to update the initramfs once everything is done syncing.

```
update-initramfs -u
```

In regards to [SnapRAID]("http://snapraid.sourceforge.net/") vs. mdadm.  mdadm is real-time RAID vs SnapRAID's Snapshot RAID.  SnapRAID is parity on top of existing disks.  This allows each disk to stand alone and to be mountable by itself.  So, even if you lose more disks than you have parity, you don't loose all of your data like in mdadm.  If performance isn't the top priority (my disks can still just about saturate gigabit), SnapRAID is probably a better solution for your use case, but I'll leave that up to you :)

---

### Post by hozzaconners on 2013-06-26
Deserved praise IMHO! When your a noob like me, advice from a master is priceless!

I've started the grow, which will take 40 hours...would've been quicker to start from scratch, but it's probably all good practice. Once it's completed I'll look at the conf file...in the meantime I'll try to learn about initramfs (just when you think you're getting somewhere someone comes along and throws in a curveball on something you've never heard of!!!) and read up on SnapRAID.

Thanks again for all the advice, hugely appreciated

---

### Post by grunge09 on 2013-06-26
plan on leaving your server "growing" your awway for 20 hours.  I have an AMD 6000+ CPU with 2GB Ram and using boad SATA II controller took 20 hours to grow.  fsck'ing takes 5-10 minutes, and reseizefs takes 10-25 minutes.  

Follow the tutorial of adding a drive nad growing it.  I have used it 2x and it works fine.  And I am about to do it a 3rd time.  

Make sure you have a good UPS on that machine doing the mdadm growing.  

And please do the last bit of updating the mdadm.conf file using the echo commands.  

Consider having another 2tb drive handy in case one goes down, don't have to have it installed as a hot spare.  Just ina closet or on a shelf.

---

### Post by CharlesA on 2013-06-26
> **grunge09 said:**
> plan on leaving your server "growing" your awway for 20 hours.  I have an AMD 6000+ CPU with 2GB Ram and using boad SATA II controller took 20 hours to grow.  fsck'ing takes 5-10 minutes, and reseizefs takes 10-25 minutes.  

Follow the tutorial of adding a drive nad growing it.  I have used it 2x and it works fine.  And I am about to do it a 3rd time.  

Make sure you have a good UPS on that machine doing the mdadm growing.  

And please do the last bit of updating the mdadm.conf file using the echo commands.  

Consider having another 2tb drive handy in case one goes down, don't have to have it installed as a hot spare.  Just ina closet or on a shelf.

Yeah, disk maintenance like growing, rebuilding, verifying can take a bit of time. I ran into issues last week that caused my array to start rebuilding after a verify failed. Took about 48 - 72 hours for the thing to finish rebuilding and that felt like an eternity while I was trying to figure out what caused the rebuild.

I would recommend a UPS on every machine... but I'm a bit crazy when it comes to protecting data/machines... :p

---

