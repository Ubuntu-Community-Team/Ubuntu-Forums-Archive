---
title: "Hardware RAID Card Help"
date: 2010-01-05
forum: Server Platforms
---

### Post by JonnyRocket on 2010-01-05
Hi, first post here.  I'm looking for some assistance in figuring out which RAID card to get.  I did some research and ended up with the Adaptec 3504, but then someone suggested going with the LSI MegaRAID SAS 9260-4i.  I took a look at it and on paper it seems like a much better piece of hardware than the 3504.  My concern is how well it works in ubuntu.  (Planning on running Karmic server)  I'm pretty sure the driver is included, but i'm getting conflicting answers on how well the storage management tool works.  Its pretty important that i can see the status of the drives and get notifications if a drive is failing from within the o/s.

I found this site while searching [http://hwraid.le-vert.net/wiki/LSIMegaRAIDSAS](http://hwraid.le-vert.net/wiki/LSIMegaRAIDSAS) which has some good info, but its confusing which cards work and which don't.

A short list of the cards i was considering:

[LIST=1]
[*]LSI MegaRAID SAS 9260-4i - Top of my list if it all works properly.
[*]3ware 9650SE-4L
[*]Adaptec 2251800-R 3405
[*]Highpoint RocketRAID 3510
[*]areca ARC-1210
[/LIST]
Has anyone had any experience with the MegaRAID in ubuntu?  What would you recommend if the MegaRAID is not a good option?

---

### Post by Krupski on 2010-01-05
> **JonnyRocket said:**
> Hi, first post here.  I'm looking for some assistance in figuring out which RAID card to get.  I did some research and ended up with the Adaptec 3504, but then someone suggested going with the LSI MegaRAID SAS 9260-4i.  I took a look at it and on paper it seems like a much better piece of hardware than the 3504.  My concern is how well it works in ubuntu.  (Planning on running Karmic server)  I'm pretty sure the driver is included, but i'm getting conflicting answers on how well the storage management tool works.  Its pretty important that i can see the status of the drives and get notifications if a drive is failing from within the o/s.

I found this site while searching [http://hwraid.le-vert.net/wiki/LSIMegaRAIDSAS](http://hwraid.le-vert.net/wiki/LSIMegaRAIDSAS) which has some good info, but its confusing which cards work and which don't.

A short list of the cards i was considering:

[LIST=1]
[*]LSI MegaRAID SAS 9260-4i - Top of my list if it all works properly.
[*]3ware 9650SE-4L
[*]Adaptec 2251800-R 3405
[*]Highpoint RocketRAID 3510
[*]areca ARC-1210
[/LIST]
Has anyone had any experience with the MegaRAID in ubuntu?  What would you recommend if the MegaRAID is not a good option?


Since you asked "What would you recommend" let me ask you... what's wrong with Ubuntu software RAID (i.e. MDADM)?

It works great and has very low CPU overhead.

I run a 4 drive RAID-5 array and even with the hard drives saturated with I/O, the CPU usage never comes off idle (using the "Conservative" governor).

For what it's worth...

---

### Post by JonnyRocket on 2010-01-05
Heh, I knew that was going to be the first response.  First first concern was processing.  I am purposely using a lower end (celeron) because I was planning on offloading the HD work to a RAID card, but it sounds like i really shouldn't be concerned?  Second concern is that I have no experience with MDADM whereas i have I have bit with hardware raid, although its was always used in Windows environments. 

Couple quick questions about MDADM:

[LIST=1]
[*]If i want to move to new hardware down the line, what is the process of moving the array?  With a hardware array, i can just unplug everything, move the drives and the card to a new machine, load drivers, and i'm good.
[*]Where is the array information stored in MDADM?  What happens if the disk controller driver no longer works for whatever reason or the array information is lost?  How do you go about getting your array back?  (I guess the same works for a hardware raid card, but it seems logical when that happens)
[/LIST]

---

### Post by Fcon_Vpro on 2010-01-06
> **JonnyRocket said:**
> Heh, I knew that was going to be the first response.  First first concern was processing.  I am purposely using a lower end (celeron) because I was planning on offloading the HD work to a RAID card, but it sounds like i really shouldn't be concerned?  Second concern is that I have no experience with MDADM whereas i have I have bit with hardware raid, although its was always used in Windows environments. 

Couple quick questions about MDADM:

[LIST=1]
[*]If i want to move to new hardware down the line, what is the process of moving the array?  With a hardware array, i can just unplug everything, move the drives and the card to a new machine, load drivers, and i'm good.
[*]Where is the array information stored in MDADM?  What happens if the disk controller driver no longer works for whatever reason or the array information is lost?  How do you go about getting your array back?  (I guess the same works for a hardware raid card, but it seems logical when that happens)
[/LIST]
Which celeron is it? Dual core celerons work great as I use one in my server. Single core celerons might struggle a bit depending on how old it is. 
I found that IDE and SATA made a bigger difference than CPU. Initially I had my OS on a 5400rpm sata drive but moved to a 7200rpm IDE drive and straight away I noticed the advantages of serial over parallel even when the sata drive is technically slower(5400rpm).

To answer your questions:

1. Just as easy as hardware raid. Plug the drives into the new system. Install ubuntu. Install mdadm. It automatically picks up your arrays. Just mount the drive or add it to fstab and boom done.
2. Not 100% sure on this. I thought Id cross this road if it ever happened to me.

So far I am sold on MDADM. I have moved the array between 2 different systems with no issues.

---

### Post by JonnyRocket on 2010-01-06
It is one of the dual cores.  An E3200.  I guess i'll read a bit more about MDADM.  I'll still have to use an add-on card since i only have 4 sata ports and 5 drives, but i still haven't sent back a fakeraid adaptec card that i ordered by mistake, so i may just use it without the raid features.

---

### Post by Krupski on 2010-01-06
> **JonnyRocket said:**
> Heh, I knew that was going to be the first response.  First first concern was processing.  I am purposely using a lower end (celeron) because I was planning on offloading the HD work to a RAID card, but it sounds like i really shouldn't be concerned?  Second concern is that I have no experience with MDADM whereas i have I have bit with hardware raid, although its was always used in Windows environments. 

Couple quick questions about MDADM:

[LIST=1]
[*]If i want to move to new hardware down the line, what is the process of moving the array?  With a hardware array, i can just unplug everything, move the drives and the card to a new machine, load drivers, and i'm good.
[*]Where is the array information stored in MDADM?  What happens if the disk controller driver no longer works for whatever reason or the array information is lost?  How do you go about getting your array back?  (I guess the same works for a hardware raid card, but it seems logical when that happens)
[/LIST]

The RAID information for MDADM is stored in "superblocks" on each drive (several copies on each drive for redundancy).

If you move the drives to a different machine, simple installing MDADM on it will cause the superblocks to be read and the array reactivated.

Alternately, you can use a command to generate the array data string:

```

root@storage:/# mdadm --detail --scan
ARRAY /dev/md0 level=raid5 num-devices=4 metadata=00.90 UUID=2d5881a9:3177604b:2e29483d:f114274d

```

The first line is the command, the second line is the output. This is the array information retrieved from the individual hard drive superblocks.

The whole configuration for MDADM is stored in a file "/etc/mdadm/mdadm.conf" and mine looks like this:

```

root@storage:/# cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=2d5881a9:3177604b:2e29483d:f114274d

# This file was auto-generated on Wed, 30 Dec 2009 19:39:46 -0500
# by mkconf $Id$

```

That's really all there is too it. Ultra simple, easy and completely reliable.

Oh by the way, your Celeron will have no problem at all handling the RAID overhead. You won't even be able to tell that CPU is being used.

Good luck.

-- Roger

---

### Post by JonnyRocket on 2010-01-06
Thanks for you're reply, Krupski.  You've pretty much backed up everything i've been reading in the MDADM manual.  So i decided to give it a shot and play around with it.  No is the perfect time since i have drives ready to go, but no data on them. And i'm running into a problem when creating the array.

First i enabled raid support:
```
modeprobe raid5
```checked to make sure its all good.  I see raid5 (and others) abvailable, but i don't see any "unused devices."  I'm not sure if i should see the 4 drives or not.
```
cat /proc/mdstat
```I can see the the 4 drives in Palimpsest.  They all look fine.  No partitions on any of them.

I run this command to create the array
```
mdadm --create --verbose /dev/md0 --chunk=128 --level=5 --raid-devices=4 /dev/sdb /dev/sdc /dev/sdd /dev/sde
```and i get
```
mdadm: failed to create /dev/md0
```I wish it would tell me why it failed so i can look into it further, but i'm not really sure where to look.  I'm sure its something simple.  Any ideas?

---

### Post by JonnyRocket on 2010-01-06
Sometimes i'm amazed at me own stupidity.  Need to be root to run that create array command.  Tried it again with sudo in front and its worked.  Its building now, at 1%.

Thanks guys!  Looks like this is going to take a while, so i'll do some performance tests tomorrow after its finished building.

[img]http://www.indyhp.com/media/pics/nas/screenshot-array.png[/img]

---

### Post by tgalati4 on 2010-01-08
LSI MegaRAID is used in Dell PowerEdge servers.  They are high performance RAID controllers.  For home use, software raid is usually sufficient if you really need RAID.  Dell has OpenManage linux tools that can read RAID status.  They were developed for Red Hat and SUSE, but they seem to work fine in Debian and Ubuntu Hardy server.

---

### Post by JonnyRocket on 2010-01-10
Ran a quick speed test on the array today using hdparm.

```
$ for i in 1 2 3; do sudo hdparm -tT /dev/md0; done

/dev/md0:
 Timing cached reads:   2272 MB in  2.00 seconds = 1135.43 MB/sec
 Timing buffered disk reads:  990 MB in  3.00 seconds = 329.70 MB/sec

/dev/md0:
 Timing cached reads:   2288 MB in  2.00 seconds = 1143.37 MB/sec
 Timing buffered disk reads:  992 MB in  3.00 seconds = 330.66 MB/sec

/dev/md0:
 Timing cached reads:   2266 MB in  2.00 seconds = 1132.44 MB/sec
 Timing buffered disk reads:  988 MB in  3.00 seconds = 329.16 MB/sec

```

I think these results are pretty good.  I'd like to see some comparisons to other arrays running MDADM too.  My 150GB Raptor drive running the OS returns an average of 88 MB/s on each test.

---

### Post by Krupski on 2010-01-10
> **JonnyRocket said:**
> Ran a quick speed test on the array today using hdparm.
.........
I think these results are pretty good.  I'd like to see some comparisons to other arrays running MDADM too.  My 150GB Raptor drive running the OS returns an average of 88 MB/s on each test.

Here's mine:

```

root@storage:/# for i in 1 2 3; do sudo hdparm -tT /dev/md0; done

/dev/md0:
 Timing cached reads:   7556 MB in  2.00 seconds = 3785.52 MB/sec
 Timing buffered disk reads:  244 MB in  3.01 seconds =  80.99 MB/sec

/dev/md0:
 Timing cached reads:   7810 MB in  2.00 seconds = 3913.26 MB/sec
 Timing buffered disk reads:  242 MB in  3.02 seconds =  80.12 MB/sec

/dev/md0:
 Timing cached reads:   7720 MB in  2.00 seconds = 3867.08 MB/sec
 Timing buffered disk reads:  236 MB in  3.02 seconds =  78.13 MB/sec

```

---

### Post by fjgaude on 2010-01-10
Here's one of my **mdadm** runs:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.38/1.36v: 4x raid5 Seagates

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec
```

The Seagates test out at about 70 MB/sec each.

---

### Post by Fcon_Vpro on 2010-01-11
Raid5: 4x Samsung 1TB 5400RPM drives
E1200 Celeron @ 1.92Ghz
Ubuntu 8.04.3 64bit

```
for i in 1 2 3; do sudo hdparm -tT /dev/md0; done

/dev/md0:
 Timing cached reads:   2462 MB in  2.00 seconds = 1231.37 MB/sec
 Timing buffered disk reads:  722 MB in  3.00 seconds = 240.65 MB/sec

/dev/md0:
 Timing cached reads:   2470 MB in  2.00 seconds = 1234.90 MB/sec
 Timing buffered disk reads:  738 MB in  3.01 seconds = 245.41 MB/sec

/dev/md0:
 Timing cached reads:   2458 MB in  2.00 seconds = 1228.87 MB/sec
 Timing buffered disk reads:  746 MB in  3.01 seconds = 248.17 MB/sec

```

My OS drive: 400GB Seagate 7200RPM

```

for i in 1 2 3; do sudo hdparm -tT /dev/sda; done

/dev/sda:
 Timing cached reads:   2464 MB in  2.00 seconds = 1232.21 MB/sec
 Timing buffered disk reads:  224 MB in  3.01 seconds =  74.47 MB/sec

/dev/sda:
 Timing cached reads:   2352 MB in  2.00 seconds = 1175.67 MB/sec
 Timing buffered disk reads:  224 MB in  3.01 seconds =  74.35 MB/sec

/dev/sda:
 Timing cached reads:   2344 MB in  2.00 seconds = 1172.04 MB/sec
 Timing buffered disk reads:  224 MB in  3.01 seconds =  74.50 MB/sec

```

---

