---
title: "New Home Backup Server"
date: 2009-02-05
forum: Server Platforms
---

### Post by sauce345 on 2009-02-05
So here is the deal. I am looking to put together a server at my house that will contain 4 TB (4 drives each 1 TB) in raid 5.  I have a fair knowledge of linux and have set up a ubuntu server before just kinda for practice without any problems.

So here is what i am wondering,  I have been reading a lot about software raid verses hard ware raid.  From what i understand software raid is legit as long you don't have a very busy server (ie running at max capacity all the time) because the hardware in machines these days can easily handle it.  Also software raid obviously does not cost anything.  Now hardware raid is said to be a bit faster and is more dedicated and the machine only sees one drive (which i like, less to screw up).  The only drawback is that a raid card that i was looking (3ware) is around 300 bucks.  What do you think?

Also just as another side note, can anybody recommend a motherboard that is linux friendly with raid?  Preferable being as cost efficient as possible.  I doubt i need much since me and only a select few with have access to it.

Any other suggestions from people who have done this and learned something from it, i would be grateful to have the knowledge pre build.

Thanks;)

---

### Post by amauk on 2009-02-05
The problem with hardware raid, is it's entirely tied to your raid card / motherboard

I run software raid (using mdadm) on my home media centre, and I can take the disks out and drop them into any other linux box and re-assemble the array, no probs

with hardware raid on a card, you'd need to take the card as well
with raid integrated on the main-board, you'd need the exact same board in another system

maybe an issue, maybe not
but I like the knowledge that if I fry my main board, I can just get another one without worrying about whether I can read my raid drives

Just for reference
2.4GHz Uni-core P4, 512Mb RAM
7 x 500Gb disks

long sustained writes (many Gb's at a time) pegs the CPU at 25%
reads don't move the CPU meter at all

Had to re-build the array twice over by media box's 5 year life-span, due to disk failures
Rebuilding took 100% CPU, and lasted for 48 hours
while rebuilding, all data was accessible, but obviously with the CPU @ 100%, performance was crap
have never lost anything
have never considered getting hardware raid

---

### Post by sauce345 on 2009-02-05
Thanks amauk 

I have been leaning toward doing the software just because of the price alone.  Their is one thing that i still don't understand about the software raid, when a drive does fail, does it notify you somehow?  I mean since it is raid it should continue to function as usual but how do i know when a disk has died?

Also it is probably a good idea to have a secondary smaller disk that is just dedicated to the OS right?

---

### Post by amauk on 2009-02-05
There's a couple of ways to set up notifications

the way I do it, is to poll the virtual device once a week from cron

```
mdadm --detail /dev/md0
```I use that command as part of a larger script that emails me once a week, detailing various bits 'n bobs.

sample output from that command is:
(hope the formatting of this doesn't screw up)
```
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Mar 12 01:03:27 2005
     Raid Level : raid5
     Array Size : 2930303616 (2794.56 GiB 3000.63 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 7
  Total Devices : 7
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Feb  5 22:06:27 2009
          State : clean
 Active Devices : 7
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : fdc696ff:4d9c3392:4cb9eff6:2461e09a
         Events : 0.40

    Number   Major   Minor   RaidDevice State
       0      22        1        0      active sync   /dev/hdc1
       1       8       81        1      active sync   /dev/sdf1
       2       8       97        2      active sync   /dev/sdg1
       3       8      113        3      active sync   /dev/sdh1
       4       8        1        4      active sync   /dev/sda1
       5       8       17        5      active sync   /dev/sdb1
       6       8       49        6      active sync   /dev/sdd1
```there's also a background daemon you can set up to automatically poll and email you,
but I've got various other things I monitor weekly, so I just lumped that command in with them and didn't bother with the separate daemon

Oh, btw
bit of advice
label your disks (write device name on sticky label and stick on side of disk casing)
first disk failure I had, spend a good hour trying to figure out which disk had gone

---

### Post by sauce345 on 2009-02-05
awesome thanks amauk, i think i have settled on software raid. Now the fun part buying all the parts.

---

### Post by amauk on 2009-02-06
> **sauce345 said:**
> Also it is probably a good idea to have a secondary smaller disk that is just dedicated to the OS right?Sorry, just seen this bit

Yes, I have a stand-alone 80Gb disk for the OS, and all apps

/dev/md0 is mounted to /media/raid5
and only stores data (films / music / etc.)

---

### Post by kpatz on 2009-02-06
> **amauk said:**
> label your disks (write device name on sticky label and stick on side of disk casing)
first disk failure I had, spend a good hour trying to figure out which disk had goneHow did you figure out which disk went with each device name?

I'd poll the array more than once a week.  Even if it only sends an email once a week, you should know about a failure sooner than that.  What if the email gets sent on Sunday, a drive fails on Tuesday, and then another drive fails on Thursday?  You're SOL, unless you knew about the 1st drive right away and got it swapped out and the array rebuilt before the 2nd drive failed.

Either use the mdadm daemon or have a cron script check the array hourly and send an email if a failure is indicated.

---

### Post by fjgaude on 2009-02-06
> How did you figure out which disk went with each device name?

One way is to use this command on each of your array drives:

```
sudo hdparm -i /dev/sd[nn]
```

Gives lots of info on the drive, the SN and its maker, etc.

---

