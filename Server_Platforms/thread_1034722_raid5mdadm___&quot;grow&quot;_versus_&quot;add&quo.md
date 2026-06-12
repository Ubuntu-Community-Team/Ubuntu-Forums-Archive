---
title: "raid5/mdadm :  &quot;grow&quot; versus &quot;add&quot;  ??"
date: 2009-01-09
forum: Server Platforms
---

### Post by ljwobker on 2009-01-09
continuing to mess around with softraid -- i've learned a ton already in no small part to the folks here. my last effort involved taking a 2-device RAID 5 array (see below) and adding a 3rd drive to it -- essentially expanding the array.

The summary of what I did:
  
[LIST=1]
[*]"grow" the raid      array in mdadm from 2 devices to 3 devices
[*]"add" the new      device to the array
[*]extend the file system
[/LIST]
  so I start with my happily humming along 2-device array. purely to speed up the various (re)building processes while I'm learning, I've been using 10GB partitions as my raid device components.... much faster than using the whole 120G disks! 

Step 1: "grow" the array up to 3 devices:
[FONT=Courier New][SIZE=3]**mdadm --grow /dev/md0 --aqds-devices=3 --verbose --backup-file /tmp/raidbak**[/SIZE][/FONT]
This takes about 5 minutes to run on my machine, and we can see the progress with:

[SIZE=3][B][FONT=Lucida Console][FONT=&quot]
[/FONT][/FONT][/B][/SIZE]
[FONT=Courier New][SIZE=3]**watch cat /proc/mdstat --and/or-- watch mdadm --detail /dev/md0**[/SIZE][/FONT]

Step 2: "add" the new device to the array. My existing array was built on /dev/sdb1 and /dev/sdc1 -- I'm adding /dev/sdd1 to it: 
**[FONT=Courier New][SIZE=3]mdadm --add /dev/md0 /dev/sdd1[/SIZE][/FONT]**
This also takes about 5 minutes ... watch it finish with the same commands as in step 1.

Step 3: resize the filesystem:
[FONT=Courier New][SIZE=3]**resize2fs /dev/md0**[/SIZE][/FONT]
ext3 can be notoriously slow, but since I'm dealing with very small filesystems this only took a few seconds.

So... this brings me to my actual question: what is step 1 doing that takes so long??? At that point, mdadm doesn't even know that /dev/sdd1 exists, so how can it be churning for that long? It appears as if it's rebuilding/extending the whole array, but there's nowhere for that data to go, right? I would expect that the delay would happen in step TWO, rather than in both. Anyone have insight into what might be going on here? (for the record, --verbose --verbose didn't help)

anyway, thanks for whatever info folks may have.

--lj




Note: (having a 2-drive RAID5 array DOES work, by the way... contrary to a lot of documentation that says you must have 3 drives to make raid 5. If you have a two-device raid 5 array, one holds the data and one holds the parity. Although the end result is sort of like raid 1, it's NOT the same thing. In a raid 1 array, both drives have identical info. In a two-device raid5 array, the parity drive will just be an XOR copy of the other drive. You can remove either drive and the raid5 array will continue to function. I chose to do it this way for two reasons: first, i wanted to see if it would work. (grin) -- second, I wanted to be able to use raid5 from the beginning, knowing that I'll be adding a 3rd drive at some point and didn't want to bother converting from raid1 to raid 5 as an intermediate step.)

---

### Post by Toet on 2009-01-09
IMHO you first add a device to the raid5 array, and then grow it. That's how I always do it. Growing means it has to rebuild. Adding means just adding a partition to the array (could also be spare).

---

### Post by fjgaude on 2009-01-09
Well, I've created two-drive raid5 arrays, but always using "missing" for the third drive during the create process.

This link is slowly becoming a bible for **mdadm**, and will get more complete the author tells us:

[http://cobraftp.serveftp.com/pub/raid.pdf](http://cobraftp.serveftp.com/pub/raid.pdf)

I believe a true raid5, with three or more drives, has equal parity on all three, and has all data on any of the two.

Perhaps when you create a two-drive raid5 without the missing than mdadm actually creates a raid1, but I doubt it. If you have good data on only one drive then I'm wrong.

Keep us informed as you your findings.

---

### Post by ljwobker on 2009-01-09
I had seen that doc, it's REALLY good.  Joe, if you're reading this... I wouldn't mind helping out with adding some more info and background to it, especially since it's got a ton of useful info already.

On the topic of two-drive RAID5: I did a lot of testing last night and you can definitely configure and run two-drive arrays very happily.  As would follow, with a two drive system you have one data drive and one parity drive.  When you add a third drive to the array, you just rebuild the whole thing : now with the data split across two drives and the parity info on the third.  I don't have a fourth disk handy, but I can't imagine it breaks.  

Another way to think about this... if I have 100GB of data:

[LIST]
[*]on a two drive RAID1 array, I would have 100GB of identical data on each drive
[*]on a two-drive RAID5 array, I would have 100GB of data on one drive, and 100GB of XOR'd parity info on the second drive.
[*]on a three-drive RAID5 array, I'd have 50GB of data on drive1, 50GB of data on drive2, and 50GB of (drive1 XOR drive2) parity info on drive3.
[/LIST]
Generalizing:  on an N-drive RAID5 array with X GB of data:

[LIST]
[*]I'd have X/(N-1) GB of data on drives 1 through N-1.
[*]On drive N, I'd have X/N GB of parity info where each stripe is an XOR of that same stripe from each drive {1 ... N-1}
[/LIST]
 
Some thoughts for anyone who happens to find the thread:  I've seen a couple of posts where people state that a two-drive RAID5 array is the same as a RAID1 array.  This is patently NOT true.  A RAID1 array has identical data on each device in the array -- in user-speak this means that you could theoretically swap any component drive for the array at any time with no loss of data.  

in a two-device RAID5 this is absolutely NOT true: one disk has the real data and the other has the parity info (which is basically an XOR copy of the first device)... but if you don't have the meta-data then the system doesn't know which drive is which, so the drives are NOT interchangeable.

Personally, I think raid1 makes sense when you want to do something like mirror a boot drive -- and you don't expect to ever grow the array.  If you're building some kind of NAS, it makes more sense to me to start with raid5 even if you only have two drives, since it's less work to add other devices in the future.

Mind you, there's nothing WRONG with having a raid1 data array, then converting it to raid5 when you need more space... it's just a couple of extra steps in the process.

---

### Post by fjgaude on 2009-01-09
I'm not sure I understand your understanding of raid5 arrays:

> on a three-drive RAID5 array, I'd have 50GB of data on drive1, 50GB of data on drive2, and 50GB of (drive1 XOR drive2) parity info on drive3.

Actually on that three drive array the array size is 200GB, not 150.

All drives within a raid5 array are identical of what is contained on each. That's my present understanding. And any two have all the data available, out of three drives.

Please e-mail Joe Bishop to get your ideas into his .pdf file. Such incease in information regarding **mdadm** is certainly an aid to all those who are starting out, and even some old hands. <smile>

---

### Post by ljwobker on 2009-01-09
you're right about where the parity info lives:  on raid5 the parity information is distributed across all drives in the array.  So in a two-drive raid5 array, each drive would have half of the real data and half of the parity info.  I had confused raid levels 4 and 5:  RAID4 uses a single disk for all of the parity info. 

Some decent references:
[http://www.pcguide.com/ref/hdd/perf/raid/levels/singleLevel5-c.html](http://www.pcguide.com/ref/hdd/perf/raid/levels/singleLevel5-c.html)

[http://www.pcguide.com/ref/hdd/perf/raid/levels/singleLevel4-c.html](http://www.pcguide.com/ref/hdd/perf/raid/levels/singleLevel4-c.html)

[http://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_5](http://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_5)

---

### Post by fjgaude on 2009-01-10
Very good we each learn new things every day, eh?

---

### Post by datarhythm on 2009-01-10
RAID5 requires 3 drives minimum. 

Here's a good thread on RAID.

[http://www.eggxpert.com/forums/ShowThread.aspx?PostID=162889#162889]("http://www.eggxpert.com/forums/ShowThread.aspx?PostID=162889#162889")

---

### Post by fjgaude on 2009-01-10
> **datarhythm said:**
> RAID5 requires 3 drives minimum. 

Here's a good thread on RAID.

[http://www.eggxpert.com/forums/ShowThread.aspx?PostID=162889#162889]("http://www.eggxpert.com/forums/ShowThread.aspx?PostID=162889#162889")

That's not really true... with **mdadm** you can build a two-drive raid5 without any trouble:

```
sudo mdadm --create /dev/md[n] level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 missing
```

This works too, if memory serves:

```
sudo mdadm --create /dev/md[n] level=5 --raid-decives=2 /dev/sda1 /dev/sdb1
```

Later, as you get the drive you would add it:

```
sudo mdadm /dev/md[n] --add /dev/sdc1
```

More study required to be sure of what you are doing, why.

---

### Post by ljwobker on 2009-01-11
with mdadm you can most certainly build a two-drive RAID5 array, without a "missing" drive.  The use case is for when you want to build a server that initially starts small (two drives) and then expand it later by adding drives to the array.  

Lots and lots of web pages state that you *must* have 3+ drives for raid5, and that simply is not true.  *most* of the use cases would imply 3+ drives, but definitely not all.

---

### Post by electrogeist on 2009-01-16
Starting out with a 2-drive RAID 5 with a "missing drive" would surely give abysmal performance running in degraded mode.

ljwobker, you may be on to something. Although pointless for most deployments, a 2-drive RAID 5 (w/o missing drive) could be helpful for the little guys starting a home server - *if* mdadm really does create it and has no issues growing it with additional drives later.  

But I almost dismissed it all after reading the misinformation in post #4.

---

### Post by fjgaude on 2009-01-16
> **electrogeist said:**
> Starting out with a 2-drive RAID 5 with a "missing drive" would surely give abysmal performance running in degraded mode.

ljwobker, you may be on to something. Although pointless for most deployments, a 2-drive RAID 5 (w/o missing drive) could be helpful for the little guys starting a home server - *if* mdadm really does create it and has no issues growing it with additional drives later.  

But I almost dismissed it all after reading the misinformation in post #4.

Well, a two-drive raid5 isn't that bad relative to performance, half one-drive write, one-drive read. I have done such some years back and it worked well. Then I added a third and that worked. I did it with relatively small drives so it didn't take that long to sync-up. Then I went to four drives, raid5. Then I started all over checking the thru-puts from array-size to array-size. Thus we learned from direct experience.

Software raid has so much felxibility and features that it takes a long time to understand what to do and when. We need a big book on the subject, covering all the things from raid0/1/5/6/10 creation, to growing, failing, replacing, etc.

---

### Post by joeinbend on 2009-09-28
Hi guys, I realize this is an old thread, and I've followed up on some similar ones recently that I've come across: I'm Joe Bishop, author of the RAID-5 Setup Guide. I've been blown away by all the great feedback received for this little guide, and I'm thrilled that so many people have found this to be useful, and I hope this has helped others get comfortable in Linux, and utilize its' value!

One comment about some of the discussion of RAID levels and physical disk requrements: You guys are correct that you can initiate a true RAID-5 array with only 2 disks, by setting one of them as "missing". PLEASE realize this kills the entire purpose of even building a RAID-5 array! A disk failure will wipe you out completely. Now, there is absolutely a place for this practice, which would be if you are shuffling around disks to build an array, you can get your RAID-5 started with 2 disks, fill the array to free up another disk, then add in that third disk to bring it out of degraded state. That's of course a highly calcuated risk!

I'm going to turn to the community for some help myself here:
I'm extending my array by adding an additional 1 TB disk, however the --grow process is EXCRUCIATINGLY slow! It's showing roughly 1000K/sec on the reshape, and the overall process will be about 11 days. Obscene. I know it's not a bus bandwidth issue, because if I fail a disk and rebuild, it does about 40,000K/sec. A friend of mine with an array built from my guide had this issue, and killed off Samba processes and VMware, and his instantly shot up to normal speeds, but not the case with mine. Has anyone else ran into this? I'd like to document it if we can narrow it down, so others don't get hit with this!

EDIT: Here's DMESG's output on the topic, when I started the --grow:

[ 2659.998141] RAID5 conf printout:
[ 2659.998148]  --- rd:5 wd:5
[ 2659.998151]  disk 0, o:1, dev:sdb
[ 2659.998153]  disk 1, o:1, dev:sdc
[ 2659.998155]  disk 2, o:1, dev:sde
[ 2659.998157]  disk 3, o:1, dev:sdd
[ 2659.998159]  disk 4, o:1, dev:sdf
[ 2659.998856] md: reshape of RAID array md0
[ 2659.998862] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[ 2659.998867] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for reshape.
[ 2659.998875] md: using 128k window, over a total of 976762496 blocks.

---

### Post by fjgaude on 2009-09-28
I personally have no experience with growing arrays... I do know that drive sizes have gotten so large that arrays take lots of time to resync. I'm not into video storage but I know many are, and they have to pay the price.

Why don't you change the min time to 20000KB/sec/disk and see what happens. In the few cases I've had to resync four 320GB drives in raid5 the speed was something like 70000KB/sec/disk but the total for the array was something like 280KB/sec as read by **gkrellm**.

Please let us know if you get more info on this.

---

### Post by joeinbend on 2009-09-30
I found the problem: There is a bug in MDADM v2.6.8, where it doesn't properly "read" the min/max speed limit settings. If you're experiencing this, edit your speed_limit_min file:
sudo nano /proc/sys/dev/raid/speed_limit_min

it probably says "1000". Change this to 40000, save and exit.

Now, if you do a "watch cat /proc/mdstat" you should see the speed increasing rapidly, and should settle down around 40,000KB/sec.

---

### Post by Xianath on 2009-09-30
joeinbend,

can you please provide a link to that bug report? I'm very interested in this issue, having recently grown an array and waited for it for 20+ hours.

Thanks,
Peter

---

### Post by joeinbend on 2009-09-30
Hi Peter,
I appologize, I shouldn't throw around the word "bug" without a verified bug report. However, it is a widely-reported problem, if you google for "mdadm bug speed_limit_min", you will find a mound of similarly-reported issues.

---

### Post by KrisWillis on 2009-10-31
Hi Joe,

First of all, great guide! It got me started with growing my 4TB RAID 5 to 5TB (and will go to 6TB when this grow has finished so I can copy the data off the remaining 1TB disk before adding it (27 hours to go!)).

In your guide, you mention the creation of an array bitmap, which I followed, but later on when I went to add another disk and then grow the array, mdadm wouldn't let me due to the device being "busy":

> mdadm: Cannot set device size/shape for /dev/md0: Device or resource busy

After a bit of research, it turns out this was due to the array bitmap - I just had to remove it before growing the array.

> sudo mdadm --grow /dev/md0 -b none

This might be worth a mention in the next version of your document, if you had one planned. Have you considered turning the document into a webpage (maybe a wiki), for ease of keeping up to date?

---

### Post by joeinbend on 2009-11-02
Hi Kris,
Thanks for the feedback, I will definitely test and add this info to my documentation. I'm glad to hear so many people are gaining Linux knowledge from this document!
As far as its' future goes, I am getting ready to launch my new web site in the next few weeks, which is largely based on my how-to documents on a broad range of topics, from Linux, computers in general, a few how-to DIY topics such as solar energy, beer brewing, etc. In the new site, all documentation will be "wiki" based.

---

### Post by ilynx on 2010-05-17
The link to joeinbend's tutorial for a RAID setup earlier in this thread is out of date.  The current link is:

[http://www.bishoptechnology.com/](http://www.bishoptechnology.com/)

Click on the Linux tab at the top of the page, then on the "Linux RAID-5 How-to" title.

 Massive thanks to Joe for all his work and help!


ilynx

---

### Post by cheryljosie on 2011-10-14
I would just like to correct a couple of misunderstandings here so that  people who stumble across this old thread do not stop here and go away  misunderstanding. The best thing is to look for more concise information  elsewhere but at the risk of duplicating info I will post my  understanding here. As an enganeer and someone who just did a months  worth of reading on Raid maybe I qualify as a pseudo-expert...

First, the question of the alleged 'bug' that slows down growing an  array (or rebuilding an array, or whatever else is going on with the  array other than normal use...)

There is no 'bug'. What is actually happening is a misunderstanding of the way the file system performance is governed.

If it exists on a dormant file server that is doing absolutely nothing,  the array will be grown/rebuilt/whatever as fast as the maximum speed  limit allows (meaning fast), possibly even if the super-user is logged in and doing minor administrative tasks.

If it exists on a busy file server that is running even a single non-super-user  process, or serving files to the intranet, or on a desktop system with a non-super-user logged in and monitoring the  rebuild every five seconds with a cron job or a script loop, the array  will be grown/rebuilt/whatever as fast as the minimum speed limit  allows (meaning slowly).

The reason for this performance is quite simple. The architects of Linux  do  not particularly care how long it takes to rebuild your array on your  out-of-box default Raid configuration. The only thing they care about is  that when you are using the  system at its default settings, you will get the best performance  possible out of your system in whatever degraded state it is in, while  still making some minimal progress on the rebuild, and noticing  absolutely no significant speed impact on any of your user processes  just because an array is rebuilding.

If you want to alter that tradeoff so that you can quickly protect  your data from a single disk failure no matter who is doing what on your filesystem, you will have to instruct your  filesystem that it is OK to make its pain known to you by slowing you  down in your other work. You will either have to increase the minimum speed  limit manually, or kill all your running user processes, and log off  everyone from the box, including your desktop session and maybe your superuser session too.

It is that simple.

So why does adding a disk or growing the array take so much more time  than growing the file system in Raid5?

If growing the partition, all that has to happen is that the partition  table is modified. If growing the file system, the superblocks and  journal have to be moved and updated. These are all fairly quick.

If adding capacity at the end of the array, all that has to happen is  that the empty space is properly initialized with zeros, because adding  zeros to parity does not change parity. Zeros are the natural Raid5  blank parity. I do not know for a fact that this is what happens but it  is what I would do. I know that Intel matrix raid has partition  information at the end of the drive too but I do not know if Linux does.

Initializing  the empty space with zeros is slow but not nearly as slow as adding a  drive.

If adding a disk or a partition from (n) to (n+1) disks,  the slices get longer by one disk/partition.  However the data still needs to be stored contiguously (linearly). As  the growth algorithm  traverses the array from start to end, all the data has to be re-aligned  to the longer slices, meaning that all the parity must be recalculated  too.

The entire array has to be re-written, sort of like a full-disk defrag.  That is going to take just as much time as reading and then writing back  the full array.

Now about two-disk Raid5...

Raid5 can have 2+ disks, but most  operating systems only support 3+ so that explains the confusion about  whether 2+ Raid5 exists. In terms of data integrity and storage capacity  there is no difference between 2 disk Raid1 and 2 disk Raid5.

Data-wise there is a difference. Rather than storing all the data  on both disks like Raid1, each disk in Raid5 stores half the data plus  parity for the other half.

Two-disk Raid5 is somewhat slower on  reads because it can only read each particular sector from one disk  rather than picking and choosing which disk to read from, and much  slower on writes or on degraded reads because of the need to do parity  calculations.

Even though the 2 disk Raid5 is sort of redundant  anyway, programming-wise and data-integrity-wise, and is a net minus  performance-wise, the creators of Linux, who provide a value product at  zero cost to people who otherwise cannot afford a quality operating  system, identified and patched a hole in the upgrade path and added a  two-disk Raid5 option in the OS.

Linux improved the process of  bringing up a Raid5 with minimal resources, meaning one disk at a time,  starting with one empty disk and a set of full disks, without taking any  hits in storage capacity or build time along the way. This can only  happen if there is a two-disk degraded Raid5 option to start off from.

The  other alternative (if there is no 2-disk Raid5 available) is to start  with a single empty disk in degraded Raid1, then copy in the first disk  of data, then add in the mirror.

At this point there is an  intermediate step of converting from two-disk Raid1 to three-disk  degraded Raid5 that has one disk worth of pre-existing data on it,  requiring a whole extra risky conversion step where redundant Raid1  mirror data is replaced with redundant Raid5 parity. This will be a slow  process and most people would prefer to avoid this delay and risk if at  all possible.

Another alternative is to just have a second empty  disk on hand to start out with an empty degraded 2-disk Raid5 array.  This skips two build steps and then the array can grow one disk at a  time, but there will be a spare disk's worth of capacity that remains  even after the last full disk is moved in. This is OK if you have the  room for an extra drive in the case, or the money to keep a spare on  hand if there is no room, but is otherwise not ideal to the  budget-minded user.

Final comment: having a 2-disk Raid5 option also means that it is possible to fully rebuild any Raid5 array from scratch without moving any data off the system and without needing to resort to any Raid1 to Raid5 conversion step. First, degrade the array by 1 disk. Second, initialize the detached disk with a degraded, reconfigured 2-disk Raid5. Third, move one disk worth of data onto the new degraded array. Fourth, shrink the filesystem on the old degraded array. Fifth, downconvert the old array by one disk and re-attach the disk to the new array. Sixth, grow the filesystem on the new array. Seventh, move on disk worth of data onto the new array...etc

This can even work if the old array has more than one loaded Raid5 (multiple partitions per disk) or any loaded mirror (Raid1) that needs reconfiguring. If it has a Raid0 loaded with data or any variant of Raid0 with Raid1, well no dice... unless you are OK leaving the Raid0 component as-is or losing the data or moving it off the array first.

Of course, all the usual backup-first caveats apply, to those who can afford to store umptydozen terabytes in two places at once and do not mind waiting weeks for the backup to complete, by which time it is obsolete anyway...

---

