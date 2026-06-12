---
title: "dmraid or should I just buy a NAS?"
date: 2011-03-16
forum: Server Platforms
---

### Post by nosebreaker on 2011-03-16
I was looking at buying a 4-bay NAS (like a Thecus N4100PRO), but then I thought maybe I should just take a spare computer and put 4 drives in it and use software raid5 instead.  The system I was going to use is a single core that runs at about 2GHz and has 1GB of RAM, which is far faster than the NAS systems I was looking at, however it is a far cry short of a modern system.

My primary concern is transfer speed across the network, I have a very old NAS now that only has 1 drive and it is painfully slow.  I'd like something much faster.

Can anyone out there that has made a 3+ disk NAS out of their Ubuntu system comment on performance numbers that they see for large files?

Right now I use 3ware 9650-SE raid controller cards for my desktop systems that have RAID, since my past experiences with software raid have been less than favorable.  I plan to use at least 4x 2TB drives.

Update: I bought parts and made my own system, then I had to adjust the parameters with blockdev to get the best speed.  Thanks to everyone!
I modified and used this script [http://ubuntuforums.org/showthread.php?p=10619689](http://ubuntuforums.org/showthread.php?p=10619689)

---

### Post by volkswagner on 2011-03-16
Hey, The Thecus N4100PRO has the same cpu as my WebDT366 tablet.

I would just like to point out that is a very efficient CPU.  It truly sips electric.

What is the power draw on your old PC.  If it is a Pent4, I'd stay away for a 24/7 file server.

If you build a unit on an Intel Atom or other low TDP CPU, it will pay for itself in a few years of electrical savings over a power hungry P4.

I may be wrong, but I think the protocol used, such as SAMBA may be the bigger contributer to slow speed vs. disk speed.  With NFS this may not be true as it is faster from my experience.

---

### Post by CharlesA on 2011-03-16
I'm not using dmraid, but the cheap-o RAID card I'm using seems to work fairly well as I'm usually getting about 50-80MB/sec usually over the network (that can hit up to 100MB/sec at times) from a 3 disk RAID-5 array.

Compare the features of the NAS unit with what you want to use the spare box for. I use my same machine that's running my NAS as a VM host as well.

---

### Post by rubylaser on 2011-03-16
I have an ( 8 ) disk mdadm RAID6 array at home.  I can transfer a Bluray rip across my gigabit network and completely saturate the connection.  I used to use an AMD 3000+ (1.8 Ghz) and I recently "upgraded" to a dual core AMD 240e.  I haven't seen any speed improvement (obviously, unless I used LACP or 10 GbE), but have seen slightly lower power usage.  I love mdadm and have been using it for years at home and work.

Here's an example of writing from my Ubuntu box to my fileserver mounted on /storage via NFS...
```
root@desktop:~# dd if=/dev/zero of=/storage/testfile.out bs=1M count=10240
10240+0 records in
10240+0 records out
10737418240 bytes (11 GB) copied, 101.421 s, 105.9 MB/s
```

That's fast enough for me :)

---

### Post by tgalati4 on 2011-03-16
I like freenas ([http://freenas.org](http://freenas.org)).  I have it running on a Pentium I, 188 MHz and 256 MB of RAM.  It will run on much less RAM.  It burns 36 watts, much more than modern NAS boxes, but freenas has a lot more flexibility than the embedded NAS roms--which (to borrow a Simpsons line) "Although physically impossible, suck and blow at the same time."

---

### Post by nosebreaker on 2011-03-16
Well the cost of those NAS devices is about $350, so it will take quite awhile of power usage to get there!  It is an AMD at 2166MHz, not sure what the model is.

Most of those cheap raid cards are actually software raid!  Do a search for "fakeraid" to see what I mean :)

---

### Post by rubylaser on 2011-03-16
Love the Simpsons quote. I've yet to see an embedded NAS put down great throughput numbers, so I couldn't agree more.  What sort of throughput do you get with that small amount of processing power?

---

### Post by nosebreaker on 2011-03-16
> **rubylaser said:**
> I have an ( 8 ) disk mdadm RAID6 array at home.  I can transfer a Bluray rip across my gigabit network and completely saturate the connection.  I used to use an AMD 3000+ (1.8 Ghz) and I recently "upgraded" to a dual core AMD 240e.  I haven't seen any speed improvement (obviously, unless I used LACP or 10 GbE), but have seen slightly lower power usage.  I love mdadm and have been using it for years at home and work.

Here's an example of writing from my Ubuntu box to my fileserver mounted on /storage via NFS...
```
root@desktop:~# dd if=/dev/zero of=/storage/testfile.out bs=1M count=10240
10240+0 records in
10240+0 records out
10737418240 bytes (11 GB) copied, 101.421 s, 105.9 MB/s
```

That's fast enough for me :)
So you saturated it with the old processor and mdadm, that is good news for me then.

100MB/s would be fantastic, right now my old crappy NAS is 1.8MB/s.  That's not a typo!
```
104857600 bytes (105 MB) copied, 58.984 seconds, 1.8 MB/s
```

---

### Post by rubylaser on 2011-03-16
Wow, I'm SURE you can expect better speeds than that with basically any solution you go with :)

---

### Post by nosebreaker on 2011-03-16
> **rubylaser said:**
> Wow, I'm SURE you can expect better speeds than that with basically any solution you go with :)

Well yes I should hope so!  I see speeds varying from 25MB/s with some NAS devices to 60MB/s on others.  100MB/s in a raid array makes sense, I'm just wondering if I should spend the $300 or not.  I have the box now, and it is on 24/7 anyway hosting my demo website and some VM's (internal use only).  I think the best bet is to just repurpose the box and get a bunch of 2TB drives and a bigger power supply and go for it with mdadm.

---

### Post by rubylaser on 2011-03-16
That's what I did, just make sure you have lots of SATA heads on the motherboard or a PCIe or PCI-X SATA controller if you need to hook up more drives than you have SATA heads on the motherboard.  I mention this, because PCI limits you 133 MB/s which has to be shared among all the drives you hook up to it. 

AND, make sure your PSU has a single rail. Otherwise, it might struggle to power up multiple drives (if you decide to contine to add more in the future).  Something like this works great...
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817139017]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817139017")

---

### Post by Sporkman on 2011-03-16
> **nosebreaker said:**
> 
100MB/s would be fantastic, right now my old crappy NAS is 1.8MB/s.  That's not a typo!
```
104857600 bytes (105 MB) copied, 58.984 seconds, 1.8 MB/s
```

Try connecting it with a different ethernet cable - the one it's using now could be defective.

---

### Post by nosebreaker on 2011-03-16
No its the NAS, its an Eagle Consus and it gives me those speeds on other ports as well.  Lots of people have complained about it.

I think it is this model:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817193041](http://www.newegg.com/Product/Product.aspx?Item=N82E16817193041)

---

### Post by nosebreaker on 2011-03-17
My old box doesn't have any SATA ports!  But looking around on Newegg I can build a much better system for much less than $300 anyway.  I'll just plan to replace this entire machine.

I think I'll build a system that is easily upgradeable.  This way if I need more RAM later I can add it (I'll start with 8GB, expandable to 16GB later).  I'll also start with 3 2TB drives, and expand them later with mdadm if I need to (I'm sure I will).  This way I can take advantage of the price savings in a year or two if I need it.  I'll also get a board that can run high-wattage quad core CPU's, but start with a budget dual core.

For my reference later if I can't fix it, the mdadm stuff is here:
[http://ubuntuforums.org/showthread.php?t=691376](http://ubuntuforums.org/showthread.php?t=691376)
[http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/](http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/)

---

### Post by tgalati4 on 2011-03-18
My P1 freenas gets 15 to 20 MB/s over a 100BaseT network.  I'm using 4 IDE drives with a Promise PCI controller.  Good enough for music and backups.

I have a gigabit router, but I couldn't get a gigabit network card to work in the P1, so I stayed with a 100BaseT card.  It's hard to mix new and old hardware and get reliable performance.

I was shopping for stand-alone NAS box and after reading the reviews, I decided to slap freenas on an old box to see what it could do.  

What I can't understand is that all of these new NAS boxes run some form of brain-dead linux with only a fraction of the features enabled.  It's 2011 people!  How about some functionality in our NAS boxen!

There are a few off-the-self NAS boxes that run freenas, but can't find the links at the moment.

---

### Post by BakCompat on 2011-03-18
I've got two boxes running FreeNAS 0.7.2.5543 with one in  single drive config and the other in a software RAID1 config. They've been operational for several months.

If you are familiar with FreeNAS, then go for it. I find it works for what it is designed to do which is a very good thing. :)

However, I'd like to have more access than is provided by FreeNAS for one of the machines. Personally, I want that box to be a full blown linux box so I can NX into it and use it for more than just file storage, as it will be sitting on an OC3 pipe. The problem it has is that it is an Intel Atom D510 mobo and is limited to 2 SATA ports onboard. They are currently occupied by two WD20EARS hard drives. In order to upgrade the box to RAID5 from it's RAID1, I have ordered a Promise TX4 SATA300 card. These are about $80 retail brand new, but are drying up. The SATA150 model is much more common and half the price. I ordered a used one on fleabay for $31.

I'll be upgrading it to a software RAID5 array running on Ubuntu or other linux distro so I can have full gui access remotely.

Do you need this capability? If not, then command line access is available for FreeNAS or linux whether it is remote or local via SSH once the server is enabled. You'll need to determine that for yourself.

The system was bought for it's low power usage, and as a dual core hyper threaded cpu, it's 4 virtual cores to linux.. During FTP xfers, I check the cpu consumption and it is about 30-40% running over it's native junky nic. I'd rather a hardware controller, but for $85, this little board has a lot to say for itself! It's a great choice for a low power box, specifically for a NAS, whether you use FreeNAS, Ubuntu, or something else. It's downside is the limitation of 2 SATA connectors, hence my purchase of a Promise TX4 - which is incidentally well supported by FreeNAS. Don't get a cheap & problematic controller like a Sil3114 chipset for this setup!!

Now in my case, this whole issue is further complicated by using WD20EARS hard drives... the WD "Green" models which natively park the heads every 8 seconds by default. I've used the WDIDLE3 utility to set that to the max value, thereby preventing the premature weardown of the heads. These drives are "Advanced Format" drives, and require specific formatting to 4k sectors, which is yet another issue complicated by their internal firmware reporting 512 byte sectors intentionally. In short, these drives will fail in HARDWARE RAID arrays, like an external dedicated NAS machine.

If, however, they are in SOFTWARE RAID, like with Ubuntu or FreeNAS, the TLER issue does not crop up, and they work fine. This is likely much of the source of many people reporting failures on WD drives on NewEgg for the better part of the last 12 months!

Hope you get your decision made well, and make sure to have a backup of your NAS, wherever you set it up on! You can do an rsync backup to a single drive or a wholly different box or whatever, but don't expect RAID to be your backup. :)

---

### Post by nosebreaker on 2011-03-27
So I decided to make my own system, and use it for VMs as well as a NAS.  I bought a generic mobo and dual-core 3GHz cpu, 8GB ram, and 3x 2tb drives to start.  The mobo has 6x SATA ports on it, so I can expand them later if need be.

I had to change the partition table on the drives from GPT to MBR, but the latest Ubuntu CD I had (10.04 desktop) wouldn't let me change the drives, so I had to go back to 9.10 and use parted to change it from gpt to msdos label first.  

Once that was done I could then configure it with mdadm for software RAID5.  After 10 hours, the drives were done syncing, and I did some speed tests.

Reading was 115MB/s, totally acceptable.
Writing was 55MB/s, kinda not acceptable.

Although this is much faster than my current NAS (anything would be), I was really hoping for faster speeds than this.  The CPU is hardly doing anything while writing, so I'm not sure if the write speeds are just from the Seagate drives or not.  I had read that others got 95MB/s and higher write speeds with the drives I chose, so to test this I am currently installing a basic system onto just one of the drives and I will do speed tests again.

I have another box, similar specs (Intel dual-core 3GHz cpu, 4gb ram, 6x 500gb drives in RAID10) but it had a 3ware 9650 hardware raid card in it (this box is maybe 4 or 5 years old).  I ran the same tests on it and got:

Reading was 161MB/s
Writing was 107MB/s

So I was kind of hoping for 100MB/s write speeds from the new system, since the old one with the old raid card was getting those speeds.  I'll post again once I do the tests on a single drive to see what the write speeds are.

---

### Post by rubylaser on 2011-03-27
Glad, you got it working first of all :) There are a few options that you can tweak that can greatly change the read/write speed.  First of all, did you set up your filesystem to match your chunk size on your array when you created it?  How do you have your filesystem mounted (any options).  And, here's the biggest thing, tweaking your device settings.  Here's an example, I assume your RAID disks are /dev/sd[bcdefgh]1

```
#!/bin/bash

blockdev --setra 16384 /dev/sd[bcd]

echo 1024 > /sys/block/sdb/queue/read_ahead_kb
echo 1024 > /sys/block/sdc/queue/read_ahead_kb
echo 1024 > /sys/block/sdd/queue/read_ahead_kb

echo 256 > /sys/block/sdb/queue/nr_requests
echo 256 > /sys/block/sdc/queue/nr_requests
echo 256 > /sys/block/sdd/queue/nr_requests

# Set read-ahead.
echo "Setting read-ahead to 64 MiB for /dev/md0"
blockdev --setra 65536 /dev/md0

# Set stripe-cache_size for RAID5.
echo "Setting stripe_cache_size to 16 MiB for /dev/md0"
echo 16384 > /sys/block/md0/md/stripe_cache_size
```

You can run some dd tests and set your stripe_cache_size, but with changing this values, you should see a significant improvement.  Hope that helps.  Also, I would expect a 6 disk RAID10 array to outperform a 3 disk RAID5 array at both reading and writing.

---

### Post by nosebreaker on 2011-03-27
Ok, so my tests with a single drive are as follows:
Write speed: 71 MB/s
Read speed: 97 MB/s

So thats not great, but not bad considering these are 5900rpm drives.

rubylaser:
Won't modifying the stripe-size on a live raid volume break it?  I'm going to replicate about 3 TB over to this system, and at 50MB/s that will take a long time, so I'd like to speed it up as much as possible.

Update: after googling a bit, the write speeds of 55 MB/s may in fact be what it should be, due to the overhead of writing for RAID5.
[http://www.z-a-recovery.com/art-raid.htm](http://www.z-a-recovery.com/art-raid.htm)

---

### Post by rubylaser on 2011-03-27
> Won't modifying the stripe-size on a live raid volume break it?
Do you mean modifying the stripe_cache_size?  If so, then no, this won't hurt a thing.  This is actually a shortened version of an init script that I run on my own array at startup to increase the read and write speed.

5900 RPM drives are certainly not speed demons, but I would expect more than 55 MB/s writing out of them even in RAID5.  You can run the commands I sent you with no concern for data loss. It will make no physical changes to your array, and will be gone the next time you restart (hence the reason, I have an init script :) ).

I actually disable Native Command Queueing on my drives as well.  Here's my actual script if you're interested...
```
#! /bin/bash

blockdev --setra 16384 /dev/sd[bcdefghi]

echo 1024 > /sys/block/sdb/queue/read_ahead_kb
echo 1024 > /sys/block/sdc/queue/read_ahead_kb
echo 1024 > /sys/block/sdd/queue/read_ahead_kb
echo 1024 > /sys/block/sde/queue/read_ahead_kb
echo 1024 > /sys/block/sdf/queue/read_ahead_kb
echo 1024 > /sys/block/sdg/queue/read_ahead_kb
echo 1024 > /sys/block/sdh/queue/read_ahead_kb
echo 1024 > /sys/block/sdi/queue/read_ahead_kb

echo 256 > /sys/block/sdb/queue/nr_requests
echo 256 > /sys/block/sdc/queue/nr_requests
echo 256 > /sys/block/sdd/queue/nr_requests
echo 256 > /sys/block/sde/queue/nr_requests
echo 256 > /sys/block/sdf/queue/nr_requests
echo 256 > /sys/block/sdg/queue/nr_requests
echo 256 > /sys/block/sdh/queue/nr_requests
echo 256 > /sys/block/sdi/queue/nr_requests

# Set read-ahead.
echo "Setting read-ahead to 64 MiB for /dev/md0"
blockdev --setra 65536 /dev/md0

# Set stripe-cache_size for RAID5.
echo "Setting stripe_cache_size to 16 MiB for /dev/md0"
echo 16384 > /sys/block/md0/md/stripe_cache_size 

# Disable NCQ on all disks.
echo "Disabling NCQ on all disks..."
echo 1 > /sys/block/sdb/device/queue_depth
echo 1 > /sys/block/sdc/device/queue_depth
echo 1 > /sys/block/sdd/device/queue_depth
echo 1 > /sys/block/sde/device/queue_depth
echo 1 > /sys/block/sdf/device/queue_depth
echo 1 > /sys/block/sdg/device/queue_depth
echo 1 > /sys/block/sdh/device/queue_depth
echo 1 > /sys/block/sdi/device/queue_depth

```

---

### Post by cariboo on 2011-03-27
Fast disk transfer speeds are wonderful, but, the real bottle neck is network transfer speeds, a network will only run as fast as the slowest device on the system. If you have a 100Mbps network the fastest transfer speed you'll see is about 12.5MB/s, this is from personal experience, I don't have any nics or switches in the 1000Mbps range so I can't attest to transfer speeds for them.

The only time fast disk transfer rates come in to play is when moving files from one disk to another.

---

### Post by rubylaser on 2011-03-27
This is a good point, but I think the poster is looking for good throughput across the network, so I assumed a gigabit network.  With some performance tweaks, good throughput is definitely possible

---

### Post by nosebreaker on 2011-03-27
> **cariboo907 said:**
> Fast disk transfer speeds are wonderful, but, the real bottle neck is network transfer speeds, a network will only run as fast as the slowest device on the system. If you have a 100Mbps network the fastest transfer speed you'll see is about 12.5MB/s, this is from personal experience, I don't have any nics or switches in the 1000Mbps range so I can't attest to transfer speeds for them.

The only time fast disk transfer rates come in to play is when moving files from one disk to another.

Yes this is on a gigabit network.  I'm well aware of Mb vs MB and how 100Mbit networking is actually 12.5MB :)  For the testing I'm just running on the local machine for now using dd:

Write test (16gb file):
dd if=/dev/zero of=testfile.out bs=1M count=16384
Read test (that same 16gb file you just made):
dd if=testfile.out of=/dev/null bs=1M

---

### Post by nosebreaker on 2011-03-27
rubylaser:

I tried your suggestion, and changing the stripe cache size from 256 to 16384 brought it down to a crawl!  The raid restore (I am doing a test) went from 52 MB/s down to 2 MB/s!  Setting it back to 256 fixes it.  I can set it to 512 with no difference, but if I set it to 1024 the speed starts dropping.  Any idea why?

The other options didn't seem to have any effect unfortunately.

---

### Post by rubylaser on 2011-03-28
What is your exact hardware in this box?  Also, if you posted earlier I might have missed it, what are the makes and models of your hard drives, and what commands did you use to both create your array, and your filesystem? (I'm wondering if they're advanced format drives, and you didn't align the partitions on them.)

Sorry for all the questions, but with 8GB of RAM, the commands I gave you should have made your array go much faster rather than putting on the brakes.

---

### Post by nosebreaker on 2011-03-28
I am using (Seagate Barracuda LP ST32000542AS 2TB 5900 RPM 32MB Cache SATA 3.0Gb/s 3.5" Hard Drive -Bare Drive):
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822148413](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148413)

The motherboard (BIOSTAR A770E3 AM3 AMD 770 ATX AMD)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813138179](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138179)

I just put in 3 different hard drives, and got similar (worse) results.  I put in a 1.5tb, 1tb, and 80gb laptop drive, created a 20gb data partition and ran the same results.  I got:
Read speed: 67 MB/s
Write speed: 43 MB/s

I also ran hdparm:
```

# /sbin/hdparm -tT /dev/md2

/dev/md2:
 Timing cached reads:    6560 MB in  2.00 seconds = 3282.08 MB/sec
 Timing buffered disk reads:  200 MB in  3.03 seconds = 65.91 MB/sec

```

Which seems to be VERY slow.

---

### Post by rubylaser on 2011-03-28
Those are advanced format drives, so that could be contributing to your problem if you didn't align the partitions.  Did you align the partitions when you set them up? They do support [Smart Align]("http://consumer.media.seagate.com/2010/06/the-digital-den/advanced-format-drives-with-smartalign/"), but I think I'd prefer to align my partitions correctly at the beginning.
```
fdisk -ul
```

And, I would agree 65.91 MB/sec is slow :)

EDIT: Apparently, this technology  provides translation between 4kB <-> 512B, but it does the alignement internally. This seems like this could potentially be worse that the jumper solution. With WD drive, you have to either use the jumper for a single partition (512b) or align sectors to be divisible by 8 with parted or fdisk. With this Seagate solution you can't do that because the firmware takes care of the alignment internally and reports the incorrect sector size to the OS. It is not clear how it works (at least to me) or how the potential problems can be worked around. But when the drive itself pushes the all sectors here and there without even reporting it to the OS, and provides incorrect information for the sake of compatibility, it could make debugging very hard to do.

---

### Post by CharlesA on 2011-03-28
That makes me so happy that the drives I use in my RAID-5 array are 512byte sector ones.

Sounds like a royal pain in the butt. :(

---

### Post by rubylaser on 2011-03-28
> That makes me so happy that the drives I use in my RAID-5 array are 512byte sector ones.
+1 this does make life a lot easier.  Or, using an Advanced Format drive that actually allows you align the partitions yourself so that you can see that they're correct.

---

### Post by CharlesA on 2011-03-28
> **rubylaser said:**
> +1 this does make life a lot easier
Definitely. I bought a couple spare drives for my array a while ago, and was glad that they were 512byte ones. I don't even want to think about what problems I'd run into if I mixed 512byte and 4K drives in the same hardware array.

---

### Post by nosebreaker on 2011-03-28
I may have fixed it!

I used fdisk to change the heads/sectors from 256/63 (old CHS/LBA settings) to 224/56 (4k setting).

In fdisk on each disk:
x for expert mode
h for heads, change to 224
s for sectors, change to 56
w to write and exit

Now speeds on a single drive were 108 MB/s for reading, and 118 MB/s for writing (old was 97/71 MB/s).  I am rebuilding the system now, will update tomorrow when its done and I can test.

This post was helpful:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-lnxw074KB-Disksdth-LX](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-lnxw074KB-Disksdth-LX)

---

### Post by nosebreaker on 2011-03-29
Right now the recovery on the fresh install is going at 62-65 MB/s, better than before but not the big increase I was hoping for.  I'm not sure if this fixed it.

---

### Post by rubylaser on 2011-03-29
At a minimum, you should be able to pass a larger stripe_cache_size to your array and see an improvement in speed.  Make sure it's a multiple of 1024 (x2 = 2048, x4 = 4096, x8 = 8192, x16 = 16384, x32 = 32768, etc).  See if any of those values increase your speed.  Also, if you create your array with an internal bitmap it would sync faster.

Seeing sync rates that high though, I would expect your array to have decent read/write speeds when it's done syncing.  Just make sure to make your filesystem's stride and stride width match up to your array's chunk size.

Finally, if you want to squeeze more performance out of your array, you really do need to play with the settings for via blockdev for your individual disks, and by setting the read ahead of the array.  Here's another script that works pretty well for tuning your array.

[http://ubuntuforums.org/showthread.php?t=1494846]("http://ubuntuforums.org/showthread.php?t=1494846")

You'll need to change the MDDEV variable to match your array (probably md0).  Just for example, here's reading and writing on my array without any tuning...
**Default**
```
root@fileserver:~# dd if=/dev/zero of=/storage/testfile.out bs=1M count=8192
8192+0 records in
8192+0 records out
8589934592 bytes (8.6 GB) copied, 120.259 s, 71.5 MB/s

root@fileserver:~# dd if=/storage/testfile.out of=/dev/null bs=1M
8192+0 records in
8192+0 records out
8589934592 bytes (8.6 GB) copied, 41.4258 s, 208 MB/s
```

**With Script I just linked to**
```
root@fileserver:~# dd if=/dev/zero of=/storage/testfile.out bs=1M count=8192
8192+0 records in
8192+0 records out
8589934592 bytes (8.6 GB) copied, 80.6329 s, 107 MB/s

root@fileserver:~# dd if=/storage/testfile.out of=/dev/null bs=1M
8192+0 records in
8192+0 records out
8589934592 bytes (8.6 GB) copied, 24.2766 s, 354 MB/s
```

I'd say that some time spent testing can really pay off :)  Remember, my array is a RAID6, so I have a fair amount of write overhead for double parity.

---

### Post by nosebreaker on 2011-03-29
My post above did not fix it, same speeds as before.  However hdparm is twice as fast (209 MB/s).  I'll try that script, thanks very much for the link.

Edit: Any idea how long this will take to run?  I modified the script, but I have no output on the screen yet.

---

### Post by rubylaser on 2011-03-30
It should run in a matter of seconds, and has at least 6 echo lines in it that would return to your terminal window when it runs.  Did you make a file and paste the script in, make it executable, and then run it as root?

```
sudo -i
```
```
nano speedup.sh
```

paste the script in. Then,
```
chmod +x speedup.sh
```
and run it.
```
. speedup.sh
```

It should look something like this when you run it...
```
root@fileserver:~# . speedup.sh 
read ahead size per device: 98304 blocks (49152kb)
read ahead size of array: 786432 blocks (393216kb)
stripe cache size of devices: 12288 pages (49152kb)
setting max sectors kb to match chunk size
setting NCQ queue depth to 1
setting stride to 256 blocks ()
setting stripe-width to 1536 blocks (6144kb)
tune2fs 1.41.11 (14-Mar-2010)
Setting stride size to 256
Setting stripe width to 1536

```

---

### Post by nosebreaker on 2011-03-30
I did yes, the CPU is doing something serious, and the HDD's are going so I thought it was doing something.

I edited the script to be more verbose and ran it again.  It seems to get stuck in the "Get all devices" section, before "get all devices and spares list".  This seems to just be parsing /proc/mdstat, which has:
```

md0 : active raid1 sdc1[2](S) sdb1[1] sda1[0]
      104320 blocks [2/2] [UU]
      
md1 : active raid5 sdc2[2] sdb2[1] sda2[0]
      32772096 blocks level 5, 256k chunk, algorithm 2 [3/3] [UUU]
      
md2 : active raid5 sdc3[2] sdb3[1] sda3[0]
      3874042368 blocks level 5, 256k chunk, algorithm 2 [3/3] [UUU]

```
md0 is my 100mb /boot, md1 is 16gb swap, and md2 is the data drive.  That is the one I edited the script to parse.  I also had to edit the lines that output to a log file.  Other than that, I didn't change the script!  Any ideas?

---

### Post by doas777 on 2011-03-30
I get much better performance from my commercially-built NAS than from my fileserver in most cases.

---

### Post by rubylaser on 2011-03-30
> I get much better performance from my commercially-built NAS than from my fileserver in most cases.

What?  Unless, you've spent a lot on a commercial NAS, those things are notoriously slow (15 MB/s - 30 MB/s).  What type of NAS do you have?

---

### Post by rubylaser on 2011-03-30
Nosebreaker, I thought you where just going to use these drives as one large array, not split them into 3 separate arrays.  That script as it's currently written won't work for you.  You'd need to echo the values like I pasted earlier or modify the script to iterate through each array to set the values.

Based on the fact that you have a RAID1 on this, I assume you're booting from this array (md0) and running two separate arrays for data.  I can see where this setup could prevent maximum speed, running the OS off the same disks in a different array as the RAID5.  60MB/s write in this scenario doesn't seem too bad to me actually.

 Based on all the SATA heads you have, I'd be interested to see the speed (if you're willing to speed the time) of the OS installed on a different disk(s) than the data RAID array.

---

### Post by doas777 on 2011-03-30
> **rubylaser said:**
> What?  Unless, you've spent a lot on a commercial NAS, those things are notoriously slow (15 MB/s - 30 MB/s).  What type of NAS do you have?
I have a synology DS209 (approx $300). 
both it an my fileserver are on gigabit links, and both operate in the 20-30MB/s range. the NAS is consistently in the upper end, and samba from my fileserver is always about 20, unless I have multiple streams going. both systems host a combination of internal SATA drives and USB 2.0 externals. the nas also seems to be able to handle multiple streams at this speed, which the server definitely cannot.

---

### Post by rubylaser on 2011-03-30
Nosebreaker is currently getting 55-60 MB/s on writes and over 100 MB/s on reads, we're just trying to get it to go faster.  For most users 20-30 MB/s is fine because they're using their NAS as a streaming server, and even at that rate streaming Bluray rips work great.

---

### Post by nosebreaker on 2011-03-30
rubylaser:

md0 is 100mb, and is only /boot
md1 is 16gb, and is swap
md2 is the rest of the drive (about 4 TB), and is / - everything is in here, including the OS as far as I know.  /etc, /var, /home...

I wanted to use it as one large array, but I couldn't get grub to boot off a raid5 array, so I configured /boot to be raid1 with a hot spare.

---

### Post by nosebreaker on 2011-03-30
Ok I debugged the script, it was expecting /dev/sd[a-z]1, and my array was /dev/sd[a-z]3, I changed those lines in the script and then it ran.

Before:
Write speed 55 MB/s
Read speed 115 MB/s

After
Write speed is 107 MB/s
Read speed is 164 MB/s

---

### Post by nosebreaker on 2011-03-30
Oh one final thing, since I ran that script, it seems the HDD's are parking the heads or something about every 10 seconds.  It looks similar to this issue:
[http://www.linuxquestions.org/questions/ubuntu-63/hdparm-apm-hard-drive-clicking-sound-588770/](http://www.linuxquestions.org/questions/ubuntu-63/hdparm-apm-hard-drive-clicking-sound-588770/)

Edit: I did the steps (ran hdparm -B 255 /dev/sd[a-c]), but I wanted to know if anyone knew of a permanent fix.

---

### Post by rubylaser on 2011-03-30
Well, I'd say that made a MASSIVE improvement in speed :)  I have no experience with those drives, but that sounds very similar to Western Digitals constant head parking.
[http://www.xlr8yourmac.com/tips/Disable_WDGreen_HeadParking.htm]("http://www.xlr8yourmac.com/tips/Disable_WDGreen_HeadParking.htm")

---

### Post by rubylaser on 2011-03-30
Okay, this looks like your problem, and a solution...
Looks like there might be a firmware update for those drives...
[http://forum.qnap.com/viewtopic.php?f=182&t=41346]("http://forum.qnap.com/viewtopic.php?f=182&t=41346")

Here's the firmware link...
[http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=213915]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=213915")

FYI: You'll want to add make an init.d or upstart script to run that script at boot, or your array will fall back to it's slow old self.

---

### Post by nosebreaker on 2011-03-30
Done, I just appended it to /etc/init.d/rc.local  Thanks!

---

