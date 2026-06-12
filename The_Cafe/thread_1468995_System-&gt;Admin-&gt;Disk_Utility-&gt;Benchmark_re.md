---
title: "System-&gt;Admin-&gt;Disk Utility-&gt;Benchmark results"
date: 2010-05-01
forum: The Cafe
---

### Post by andrewabc on 2010-05-01
Only works in ubuntu 10.04
[Original thread](http://ubuntuforums.org/showthread.php?t=1464114) - forum closed so I thought I'd create one here.

Post your read benchmark results.

Don't do read/write as I have no idea if writing is safe.

Are the results what you are expecting? Better/worse than manufacturer suggest, or other benchmarking programs?

Make sure to list your HDD or SSD model/size.
Post a screenshot or text version. **ALT+print screen to get just benchmark window.**

---

### Post by Brent0 on 2010-05-01
I'm using a Western Digital Caviar Blue - [http://www.newegg.com/Product/Product.aspx?Item=N82E16822136098](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136098)

Here are the results: 
[ATTACH]155084[/ATTACH]

It's actually a little better than I thought, considering it's such a cheap HDD. ($47.99)

---

### Post by standingwave on 2010-05-01
Western Digital Caviar SATA Hard Drive 640 GB, 16 MB Cache, 7200 RPM

---

### Post by theeldest on 2010-05-02
This is 4x 640GB Western Digital AAKS (Blue) in a RAID5 setup:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=155172&d=1272816298[/IMG]

---

### Post by Merk42 on 2010-05-02
These seem low :(

Master - Seagate Barracuda 160GB, 16MB cache, 7200 RPM
[ATTACH]155176[/ATTACH]

Slave - Maxtor Diamondmax 160GB, 8MB cache, 7200 RPM
[ATTACH]155177[/ATTACH]

---

### Post by NMFTM on 2010-05-02
Results of two Samsung [Spinpoint F3 1TB]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152185&cm_re=Samsung_Spinpoint_F3-_-22-152-185-_-Product") hard drives fake RAID0'd together using JMicron's JMB362 hard drive controllers.

---

### Post by theeldest on 2010-05-02
Merk, 

Those numbers are about right. The speed you get is based on platter density. Since the drives you've got are a somewhat older design (even if the drive itself is new), the amount of data on a single drive is low compared to the newer 1TB+ drives. Here are my results from HD Tune (windows 7) for a few different drives

Maxtor 250GB
Min 34.4 MB/s
Max 67.3 MB/s
Ave 54.3 MB/s
A T 15.0 ms

Maxtor 100GB
Min 16.1 MB/s
Max 62.4 MB/s
Ave 47.6 MB/s
A T 21.3 ms

Samsung 400GB
Min 30.5 MB/s
Max 70.9 MB/s
Ave 54.4 MB/s
A T 14.1 ms


Also, if you'd like to compare your results, here's a good thread with listings using HD Tune (similiar windows benchmark).
[http://forums.techpowerup.com/showthread.php?t=68546]("http://forums.techpowerup.com/showthread.php?t=68546")

---

### Post by andrewabc on 2010-05-02
Anyone with a netbook with the default 160gb/250gb 5400rpm results?

Would be nice to know those. Also would be nice to know what happens when replaced with decent 30gb SSD. If it can speed up lots of or SATA or overhead doesn't allow full speed on netbook models.

@merk42
For a 160gb drive that's not bad at all.

Here is mine from 4 year old:
320gb Hitachi 7200rpm 8mb cache
min 37.2
max 78.5
avg 63.9
access time 13.6 ms

---

### Post by happyhamster on 2010-05-02
64GB OCZ Agility SSD

Min 144.9
Max 216.6
Avg 185.7
AT  0.3 ms

---

### Post by markp1989 on 2010-05-02
My ocz 32gb vertex SSD

Minimum Read Rate: 78.3  MB/s
Maximum Read Rate: 191.5 MB/s
Average Read Rate: 124.3 MB/s
AT: 0.2 ms

for some reason the disk utility thinks its a PATA drive not a SATA Drive, so i dont know if that affects results atal

---

### Post by happyhamster on 2010-05-02
32GB OCZ Vertex SSD, ext3 (benchmark run from a live session)

Min 77.2
Max 259.3
Avg 154.3
AT 0.1 ms 

40GB Intel X25-V SSD, ext3 (live session)

Min 162.1
Max 281.0
Avg 242.0
AT 0.2 ms

---

### Post by andrewabc on 2010-05-02
> **markp1989 said:**
> for some reason the disk utility thinks its a PATA drive not a SATA Drive, so i dont know if that affects results atal

That's a bug. It lists every device (HDD or SSD) as PATA or ATA.

---

### Post by NightwishFan on 2010-05-02
My average read rate was 85mb/s my average seek time was 23ms. I am not sure if it differs by scheduler, but the anticipatory scheduler got the best results, followed by CFQ.

---

### Post by vikrant82 on 2010-05-02
There's your average 5400 rpm.

---

### Post by P4man on 2010-05-06
Here is a result you havent seen yet: Not another boring hdd or SDD;
[SIZE="5"]
**15 el cheapo 2 GB thumbdrives in RAID 0**[/SIZE]

[[img]http://www.ubuntu-pics.de/thumb/57893/usbsticks_ZuK0no.jpg[/img]](http://www.ubuntu-pics.de/bild/57893/usbsticks_ZuK0no.jpg)

( 4 more in the back of my PC)


[[img]http://www.ubuntu-pics.de/thumb/57894/raid_Vt4iP1.png[/img]](http://www.ubuntu-pics.de/bild/57894/raid_Vt4iP1.png)


[[img]http://www.ubuntu-pics.de/thumb/57898/15x2_raid_0_f01oo5.png[/img]](http://www.ubuntu-pics.de/bild/57898/15x2_raid_0_f01oo5.png)

---

### Post by earthpigg on 2010-05-06
LOL, that's pretty epic.

but, i must ask, ***why?***

---

### Post by Miguel on 2010-05-06
I had to post, I really had to, because P4Man's post is full of win. Pure and epic win. BTW, are the USB keys in RAID-0 or 5? One of the windows hints it's actually RAID-5. Not that it will matter much, though. But writing 20 MB/s in those keys... EPIC!!!!!

---

### Post by Mr. Picklesworth on 2010-05-06
> **P4man said:**
> Here is a result you havent seen yet: Not another boring hdd or SDD;
[SIZE="5"]
**15 el cheapo 2 GB thumbdrives in RAID 0**[/SIZE]

( 4 more in the back of my PC)

*Gasp* *Amazing idea*. I've always wanted to play with a RAID setup. Never thought to use flash drives! :D


Palimpsest's graph could really use a legend, and axis labels, for people like me who are new to the disk benchmarking world. (Or who are just picky about graphs). What's the crazy green stuff all about?

---

### Post by andrewabc on 2010-05-06
> **Mr. Picklesworth said:**
>  What's the crazy green stuff all about?
It is the average access time (bottom right benchmark#).

Yep, they need to clean up the graphs more.

That USB raid is cool.

---

### Post by cariboo on 2010-05-06
Somethings broken

---

### Post by cariboo on 2010-05-06
Here's something a little more mundane, 5400RPM 160GB SATA

---

### Post by andrewabc on 2010-05-06
> Here's something a little more mundane, 5400rpm 160Gb SATA:
Nothing shows up. When I quote your post, quote doesn't show up when replying. had to copy/paste your text.

What is this 160gb in? netbook/nettop?

Hmm, looks like you double posted and your second image attachment is broken.

---

### Post by cariboo on 2010-05-06
Something seems to be broken at the moment, I can't get rid of my double post, and the images I upload don't show up. The drive is in my netbook.

---

### Post by P4man on 2010-05-07
> **earthpigg said:**
> LOL, that's pretty epic.

but, i must ask, ***why?***

You mean why **NOT** ?

My brother was given a bag full of branded sticks to hand out to customers. When I saw all those sticks i figured I had to do something fun with them :)

> 
 BTW, are the USB keys in RAID-0 or 5? One of the windows hints it's actually RAID-5. 

I did both. More benchmarks with raid 0 and 5 here:
[http://ubuntuforums.org/showthread.php?t=1474453](http://ubuntuforums.org/showthread.php?t=1474453)

Now Im struggling to boot from the array. Installing ubuntu on it was easy, but the bios will not initialize any sticks (or other devices, even keyboard) from the PCI USB controller. It requires a driver / kernel before even a keyboard attached to it becomes usable.

So I moved them all the sticks to my onboard USB, only to find out my bios only initializes 6 drives. No more. So I put grub and the kernels on a separate 16th stick, but I cant select it in the boot menu lol (only shows 6 and always 6 from the raid arary). 

If I disconnect the hubs with the raid, i can boot from the 16th stick with grub, but when i reconnect them its already too late and grub complains the raid doesnt exist

 May need a supergrub CD (since I can select the CD as boot device separately from all the sticks/hdds).

---

### Post by Khakilang on 2010-05-07
Here's mine.
):P

[ATTACH]155836[/ATTACH]

---

### Post by andrewabc on 2010-05-07
8 year old 80gb

@cariboo907
attachment is working now.

---

### Post by Frogs Hair on 2010-05-07
WD Caviar Blue 500 gb

---

### Post by tilapia on 2010-05-09
Here's mine. It's an XPS M1330 with an 80GB Intel SSD. 

Minimum Read Rate: 224.1 MB/s
Maximum Read Rate: 283.4 MB/s
Average Rad Rate: 268.1 MB/s
Average Access Time: 0.2ms

Must get a pair of these to RAID 0 for my main rig!

---

### Post by 98cwitr on 2010-05-09
Basic 500GB Seagate 7200rpm SATA 3.0Gbps drive

---

### Post by andrewabc on 2010-05-09
> **tilapia said:**
> Must get a pair of these to RAID 0 for my main rig!

As far as I know if you RAID SSD, TRIM will not work.

Indilinx chipset SSD have garbage collection which helps with this. Intel only has TRIM.

So you'll get the speed improvement RAIDing two intel SSD, but no TRIM won't help with maintenance.

@98cwitr
Can you crop your image so only the benchmark window is showing? alt+print screen takes screenshot of your current selected window for future reference.

---

### Post by Phrea on 2010-05-09
8MB cache.

It seems rather sluggish...

---

### Post by cariboo on 2010-05-09
I have Two Seagte 250Gb drives in this system, 1 PATA and 1 SATA. Can you tell which one is which?

---

### Post by Phrea on 2010-05-09
> **cariboo907 said:**
> I have Two Seagte 250Gb drives in this system, 1 PATA and 1 SATA. Can you tell which one is which?

I wonder why other some of you have such faster disks than mine... I just put it in yesterday, and although it's only a 160GB [SATA II] disk, it shouldn't be as slow as it is.
I'll do this test on my other box too, tomorrow, it's got a 320GB disk, maybe that's a bit faster.

---

### Post by andrewabc on 2010-05-09
> **Phrea said:**
> 8MB cache.

It seems rather sluggish...

What is your harddrive?
You cut out the window title bar when cropping image. So we have absolutely no idea what hard drive you have.

> **Phrea said:**
> I wonder why other some of you have such faster disks than mine... I just put it in yesterday, and although it's only a 160GB [SATA II] disk, it shouldn't be as slow as it is.
I'll do this test on my other box too, tomorrow, it's got a 320GB disk, maybe that's a bit faster.

You're benchmark was better than the person you just quoted.
Starting off at 115mb/s is pretty good. I just slows down a lot as you get near end of disk. Is your 160gb disk 5400rpm or 7200rpm? On a laptop or desktop? Some older laptops have SATAII but have it disabled (so only SATAI) to save power. Although only noticeable with SSD since they get up to 250mb/s (but don't due to sataI limitation).

@cariboo907
I have no idea which is sata or pata.
You're 81mb/s average disk is kinda weird at first being slow.
No idea

---

### Post by cariboo on 2010-05-09
I may have left the speed limiting jumper on the SATA drive, I never thought to check.

---

### Post by 98cwitr on 2010-05-14
40gb old a$$ drive i am using to image for my ssd thats on the way...partimage doesnt resize large partitions ftl

[img]http://img.photobucket.com/albums/v673/98cwitr/Screenshot-40GBHardDiskATAST340015A.png?t=1273876422[/img]

---

### Post by Viva on 2010-05-14
:(

---

### Post by andrewabc on 2010-05-14
> **Viva said:**
> :(

Thanks for the benchmark. Looks like netbook based upon screen resolution. EDIT: cd/dvd drive? guess not netbook.

What's the 80gb hard drive you also have running?

---

### Post by Viva on 2010-05-14
It is a PC. The 80GB hard drive is a 6 year old HDD I'm planning to sell.

---

### Post by ubunterooster on 2010-05-14
128Gb patiot torqx

---

### Post by Phrea on 2010-05-14
> **andrewabc said:**
> What is your harddrive?
You cut out the window title bar when cropping image. So we have absolutely no idea what hard drive you have.



You're benchmark was better than the person you just quoted.
Starting off at 115mb/s is pretty good. I just slows down a lot as you get near end of disk. Is your 160gb disk 5400rpm or 7200rpm? On a laptop or desktop? Some older laptops have SATAII but have it disabled (so only SATAI) to save power. Although only noticeable with SSD since they get up to 250mb/s (but don't due to sataI limitation).

It's a WD 160GB 7200rpm 3.5" disk in a desktop machine. Not sure, but I think it has 8MB cache.

Benchmarked my other system hdd too, it's a bit faster, see attachment.

---

### Post by Phrea on 2010-05-14
> **cariboo907 said:**
> I may have left the speed limiting jumper on the SATA drive, I never thought to check.

Wait, SATA drives have speed limiting jumpers...?
All of them or just certain brands/types?

---

### Post by cguy on 2010-05-15
2 x Samsung Spinpoint F3 500GB (no RAID)


I'm really curious to see the benchmarks of some Caviar Blacks.

---

### Post by McRat on 2010-05-15
32bit 10.04: WD Blue  320gb 89.2mbs read avg, and 15.2 msec seek.
32bit 10.04: WD Black 1.0TB 95.7mbs read avg, and 12.0 msec seek.
32bit 10.04: Hitachi 500bg 114.6mbs read avg, and 19.4 msec seek.
32bit 10.04: Seagate 750gb 66.8mbs  read avg, and 13.7 msec seek.


Out of the drives I have sitting here, I'd have to go with WD Black.  No, it's not the fastest read, but it's seek time is way shorter.  If you have small or fragmented files, it's probably going to do the best.

The Hitachi 500gb is $44 at Fry's, and would be the best for streaming video.

---

### Post by cariboo on 2010-05-15
> **Phrea said:**
> Wait, SATA drives have speed limiting jumpers...?
All of them or just certain brands/types?

Some Seagate drives have jumpers to limit the data transfer speeds to maintain backwards compatibility with motherboards that don't support SATAII. The last Seagate 750GB Drive I bought about 6 months ago had a transfer speed limiting jumper.

---

### Post by Phrea on 2010-05-15
> **cariboo907 said:**
> Some Seagate drives have jumpers to limit the data transfer speeds to maintain backwards compatibility with motherboards that don't support SATAII. The last Seagate 750GB Drive I bought about 6 months ago had a transfer speed limiting jumper.

Thanks.
I've got a few WD disks here, amongst some others, I'm definitely checking out if my drives have this setting.

---

### Post by toupeiro on 2010-05-15
OCZ APEX_SSD, single disk, no raid, no custom elevator, just default grub.cfg for ubuntu 10.04

---

### Post by McRat on 2010-05-15
> **cariboo907 said:**
> Some Seagate drives have jumpers to limit the data transfer speeds to maintain backwards compatibility with motherboards that don't support SATAII. The last Seagate 750GB Drive I bought about 6 months ago had a transfer speed limiting jumper.

Yes.  I tried to take a picture, but my camera wouldn't focus.

If you are holding the drive label up, and looking at the connector end, you jumper the two pins on the right (outboard) to kick it into 1.5gbs mode (slow).  No jumper?  AOK.

---

### Post by Phrea on 2010-05-15
I believe some of my drives do have jumpers, I'll just yank 'em all out. :D

---

### Post by McRat on 2010-05-15
> **cguy said:**
> 2 x Samsung Spinpoint F3 500GB (no RAID)


I'm really curious to see the benchmarks of some Caviar Blacks.

See post right below you.  Blue 320gb vs Black 1TB.  In that case, not too much difference excp seek time.

---

### Post by ubunterooster on 2010-05-15
> **McRat said:**
> Yes.  I tried to take a picture, but my camera wouldn't focus.

If you are holding the drive label up, and looking at the connector end, you jumper the two pins on the right (outboard) to kick it into 1.5gbs mode (slow).  No jumper?  AOK.
Your camera likely needs to be set to "macro mode" see the manual for info as that differs from cam to cam.

---

### Post by Paqman on 2010-05-16
I <3 my Intel SSD:

---

### Post by theeldest on 2010-05-16
> **Phrea said:**
> I believe some of my drives do have jumpers, I'll just yank 'em all out. :D

You can probably just leave the jumpers alone. Even if they're jumpered to the 'slower' SATA I, you're still only 'limited' to 187 MB/s.

Sure, you'll hit that barrier with a RAID setup or an SSD, but not single mechanical disk will have a problem from that jumper being in the 'slow' setting.

---

### Post by 98cwitr on 2010-05-19
Mushkin 60GB SSD, fresh install

[IMG]http://img.photobucket.com/albums/v673/98cwitr/Screenshot-60GBSolid-StateDiskATAMu.png[/IMG]

---

### Post by mihai.ile on 2010-05-19
My laptop's Segate Momentus 500GB 5400.6 SATA (ST9500325AS)

EDIT: updated the image, now contains write test also (did it from ubuntu live usb after I deleted the whole partition)

---

### Post by WaVeR on 2010-05-20
Western Digital Black (No raid)

---

### Post by mihai.ile on 2010-05-21
Just got an Kingston SSD snv125 128GB (I ordered the snv425 version which is much better but the shop sent me this older one... grrrr)
Anyway it is an improvement from my HDD on 2 posts above (I think lol as writes are quite bad but the system is way faster so...)

Enough talking, here are the results (once again from ubuntu live usb with the drive empty)

---

### Post by stmiller on 2010-05-23
WD Blue is my boot drive. I need an SSD! :)

[[IMG]http://imgur.com/6gqsJ.png[/IMG]](http://imgur.com/6gqsJ.png)

---

### Post by MechaMechanism on 2010-05-23
2 750GB Hitachi hard drives.
EXT4
RAID 0
Ubuntu 10.04
Vast improvement over single drive use.

[[IMG]http://img710.imageshack.us/img710/4402/benchmark0.th.png[/IMG]]("http://img710.imageshack.us/i/benchmark0.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by 98cwitr on 2010-05-24
> **mihai007 said:**
> Just got an Kingston SSD snv125 128GB (I ordered the snv425 version which is much better but the shop sent me this older one... grrrr)
Anyway it is an improvement from my HDD on 2 posts above (I think lol as writes are quite bad but the system is way faster so...)

Enough talking, here are the results (once again from ubuntu live usb with the drive empty)

is that a fresh reformat? That looks quite low :(

---

### Post by mihai.ile on 2010-05-24
yes it is low, because I got the first generation of kingston SSD instead of the fourth one... bad luck, they offered a refund of 30&#8364; because you know old tech here in SSD area does not get very cheap, it just dissapears/replaced by newer.
Anyway I am glad that it is still way better than my 500GB hdd of which I posted the results in a post above the ssd ones.

---

### Post by TheeMahn2003 on 2010-05-31
1 X [Adata 32 GB SSD]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820211419") (flashed to 1848 firmware):

Min: 198.9 MB/s
Max: 263.7 MB/s
Avg: 223.5 MB/s

[Screenshot]("http://img706.imageshack.us/i/adatassd.png/")
[[IMG]http://img706.imageshack.us/img706/9580/adatassd.th.png[/IMG]](http://img706.imageshack.us/i/adatassd.png/)


Boots in 7.6 seconds
[[IMG]http://img525.imageshack.us/img525/6283/sledgehammerlucidboot.th.png[/IMG]](http://img525.imageshack.us/i/sledgehammerlucidboot.png/)

I will buy a second one to raid them.

---

### Post by andrewabc on 2010-05-31
> **TheeMahn2003 said:**
> 1 X [Adata 32 GB SSD]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820211419") (flashed to 1848 firmware):

Min: 198.9 MB/s
Max: 263.7 MB/s
Avg: 223.5 MB/s


I did some quick research on that product. I can not find anywhere what controller it uses. I assume it is Indilinx?

---

### Post by TheeMahn2003 on 2010-05-31
> **andrewabc said:**
> I did some quick research on that product. I can not find anywhere what controller it uses. I assume it is Indilinx?

I believe you are correct:
The description on A-Data’s site mentions a lot of different performance enhancements compared to “regular SSDs.” The device is powered by Indilinx’s current controller together with 64MB cache memory, which, according to A-Data, leads to 250 MB/s maximum read (230 MB/s for 32GB and 64GB versions) and 170 MB/s maximum writes (150 MB/s for 32GB and 64GB capacities).

That is about the speeds I was getting before flashing the drive, which is a pain in the rump.

---

### Post by TheeMahn2003 on 2010-05-31
> **98cwitr said:**
> is that a fresh reformat? That looks quite low :(

Your drives thoughput is higher then mine, however your access time a different story (the green dots).  Is your drive slc or mlc?

Do you use bootchart?  I would like to see your results.

```
sudo apt-get install bootchart
```

reboot goto /var/log/bootchart/ and post the screenie it generates.

---

### Post by TheeMahn2003 on 2010-06-04
I thought I would come back and post what I have learned with SSD's this is the first of many more I will purchase.  SSD's slow down over time, never to the speed of a regular Hard disk, but none the less they [slow down]("http://www.anandtech.com/show/2738"), a long read, the guy knows what he is talking about.  There is only one way to restore the speed and it is not re-installing Ubuntu, this will actually also slow it down.

Even a SSD with trim support will also slow down, yes [Trim support]("https://wiki.ubuntu.com/KernelTeam/Specs/KarmicSSD") is in Lucid:

```
theemahn@SledgeHammer:~$ sudo hdparm -I /dev/sda1
[sudo] password for theemahn: 

/dev/sda1:

ATA device, with non-removable media
	Model Number:       A-DATA SSD                              
	Serial Number:      0607T3J6B0AA5F4I788T
	Firmware Revision:  FW1848  
Standards:
	Supported: 8 7 6 5 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:   62533296
	LBA48  user addressable sectors:   62533296
	Logical  Sector size:                   512 bytes
	Physical Sector size:                   512 bytes
	device size with M = 1024*1024:       30533 MBytes
	device size with M = 1000*1000:       32017 MBytes (32 GB)
	cache/buffer size  = unknown
	Nominal Media Rotation Rate: Solid State Device
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 1	Current = 1
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	    	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	DOWNLOAD_MICROCODE
	    	SET_MAX security extension
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Phy event counters
	    	DMA Setup Auto-Activate optimization
	    	Device-initiated interface power management
	   *	Software settings preservation
	   *	Data Set Management determinate TRIM supported
Security: 
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
	not	supported: enhanced erase
Checksum: correct
theemahn@SledgeHammer:~$ 

```

Note the 	   *	Data Set Management determinate TRIM supported

This slows down this happening, but eventually the end results are the same.

I now see:
Min: 96.9 MB/s
Max: 256.3 MB/s
Avg: 170.2 MB/s

Compare it to my numbers above.


What Happened?  Read the whole 20 page article posted above.  The real question is how do I fix it...

No, we do not need windows to fix it hdparm is a wonderful tool.  I do not care if you use UE or Ubuntu just booting a live disk and wiping the drive will restore full speed.  I hope you read the full article about SSD's then you would know that you can only do this ~ 10,000 times before errors begin to appear.

I will not take any responsibility if you wreck your SSD, but here is your [answer]("https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase").

I just thought maybe I could help a few ppl out.  I typically do not have the time to do so.

---

### Post by andrewabc on 2010-06-04
The whole "SSD slow down over time" aka "used state" has been fixed since that article was written. Yes they do slow down a bit, mostly when drive is near full capacity.

TRIM and garbage collection on Indilinx drives almost completely fix this problem. Although a clean wipe using various utilities they provide put drive back to 'brand new state'.

I havn't seen much new vs used benchmarks since 2009.

With new sandforce controllers if you constantly benchmark it the speed will decrease and it will take longer for it to recover.
Or say a new drive and you install OS and a bunch of programs, it will be slow at first, but should speed back up to near original in a couple days. Just make sure to trigger (in windows) a TRIM, by deleting a file (a simple notepad file suffices). Empty recycle bin.

---

### Post by TheeMahn2003 on 2010-06-08
O.k.  I can beat on a hard disk believe it.   Is the below a years work on the drive?

---

### Post by andrewabc on 2010-06-09
> **TheeMahn2003 said:**
> O.k.  I can beat on a hard disk believe it.   Is the below a years work on the drive?

What is the brand and firmware on the drive? For firmware have you upgraded it any? Is it still using same firmware as when you bought it 1 year ago?

---

### Post by libssd on 2010-06-29
> **andrewabc said:**
> Anyone with a netbook with the default 160gb/250gb 5400rpm results?

Would be nice to know those. Also would be nice to know what happens when replaced with decent 30gb SSD. If it can speed up lots of or SATA or overhead doesn't allow full speed on netbook models.

@merk42
For a 160gb drive that's not bad at all.

Here is mine from 4 year old:
320gb Hitachi 7200rpm 8mb cache
min 37.2
max 78.5
avg 63.9
access time 13.6 ms
Here are figures from an Acer AA1 D150; I'm pretty sure that throughput is constrained by SATA I bus. Ubuntu 10.04, ext4, some performance tweaks applied.

```
ATA device, with non-removable media
	Model Number:       OCZ-VERTEX                              
	Firmware Revision:  1.4     
Standards:
	Supported: 8 7 6 5 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
```

---

### Post by andrewabc on 2010-06-29
> **libssd said:**
> Here are figures from an Acer AA1 D150; I'm pretty sure that throughput is constrained by SATA I bus. Ubuntu 10.04, ext4, some performance tweaks applied.

Thanks for the info.

I guess the sequential speed is still twice that of the default hard drive, and as long as random 4k are better you would still get much faster speeds.

Hopefully in the next round of netbook updates they have sataII speeds. I don't see the reason for artificially  disabling sataII, especially when battery times are very long for netbooks, I doubt the extra power used for sataII would make much of a difference.

I bought 60gb vertex for $125 this past weekend, and I'll be putting in old eeebox. Will post results here. As far as I can tell it should have SATAII.

---

### Post by cmeek on 2010-07-04
This is for my 160GB Western Digital drive that I recently added to my old laptop to replace a failed drive. Does anyone know why there is the precipitous drop in throughput at the 85% point? And is there a way to fix that?

The laptop is a Toshiba A25-S279 that is about 6 years old. And the hard drive is a WD16000BEVE.

---

### Post by Xianath on 2010-07-04
12 Samsung SpinPoint F1 1TB disks in software RAID6. I have no GUI on this server so I just ran the udisk benchmark helper utility and converted the results to CSV to get a nice graph.

And before anyone tries this, **[COLOR="Red"]THE WRITE TEST IS DESTRUCTIVE![/COLOR] **(No, I didn't try it on my RAID :) ).

---

### Post by andrewabc on 2010-07-04
60gb ocz vertex in eeebox b202
Seems limited to SATAI

[here](http://img442.imageshack.us/i/screenshot160gbharddisk.png/) is the 160gb HDD that was in it before.

So even though limited to SATAI, my read speeds are at least twice as fast.

Not really worth it at current prices (I paid $130 CAD for it) to put in that old of hardware, but once say 60gb stays below $100, I don't see much reason to use slow HDD in laptops/netbooks/nettops, as long as you have external storage. Which you can get 1 terabyte 3.5" for $70-80, and an enclosure for $40.

---

### Post by Theft42 on 2010-07-04
Seagate Barracuda 3.5" Internal Drive
500 GB
16 MB Cache
7200 RPM

---

### Post by CDR Services on 2010-07-13
New 64 Gig Kingston SSD with a fresh install
[ATTACH]163267[/ATTACH]

---

### Post by andrewabc on 2010-08-12
> **cmeek said:**
> This is for my 160GB Western Digital drive that I recently added to my old laptop to replace a failed drive. Does anyone know why there is the precipitous drop in throughput at the 85% point? And is there a way to fix that?

The laptop is a Toshiba A25-S279 that is about 6 years old. And the hard drive is a WD16000BEVE.

No idea how to fix it, but could be good idea to partition your HDD to avoid that area of the disk so you don't ever get any files put on that slow part of HDD.

Appears to happen around 85% mark of HDD, So I would leave the last 20%-25% of HDD unpartitioned to try and make sure nothing gets placed there. Unless you really need the space. But if that area is defective, then you would be better off not using that space.

So probably when formatting/installing in future, manually format everything, and only create filesystem for only 120gb, that would start at first, leaving the end not used, and thus not use slow area of disk. Some people already do this with normal HDD, to put OS/apps partition near front of HDD where fastest, adn then create another partition for last 1/2 of HDD for media and stuff that doesn't need to be fast.

---

### Post by happyhamster on 2010-08-26
This is weird. Just re-tested my Vertex SSD, and the results are much better compared to ~4 months ago.

32GB OCZ Vertex SSD, ext3 (benchmark run from Maverick Meerkat)

Previous result:
Min 77.2
Max 259.3
Avg 154.3
AT 0.1 ms 

Current:
Min 194.3
Max 250.8
Avg 232.2
AT 0.3 ms 

I did do a firmware upgrade (to version 1.5), and it has a (sort of) fresh ubuntu on it, so perhaps that accounts for it. It's a huge difference though. Never used any tools to clean the drive either.

---

### Post by CraigPaleo on 2010-08-26
I'm downloading an ISO. I'm not sure how much that would effect it.

---

### Post by samalex on 2010-08-26
Here's mine from my System76 PanP5 laptop running a 500 Gig 7200 RPM Seagate drive ST9500420AS.



Sam

---

### Post by andrewabc on 2010-08-28
> **happyhamster said:**
> This is weird. Just re-tested my Vertex SSD, and the results are much better compared to ~4 months ago.

32GB OCZ Vertex SSD, ext3 (benchmark run from Maverick Meerkat)

I did do a firmware upgrade (to version 1.5), and it has a (sort of) fresh ubuntu on it, so perhaps that accounts for it. It's a huge difference though. Never used any tools to clean the drive either.

Depends on what your previous firmware was. Maybe TRIM was triggered (if using newer kernel or 10.10), or garbage collection had time to work. Glad it is working better.

---

### Post by markp1989 on 2010-10-12
here is my super talent ssd:

---

### Post by elliotbeken on 2011-04-07
[IMG]http://elliotbeken.com/img/SD%20Card%20Banckmark.jpg[/IMG]

---

### Post by ezzatron on 2011-06-02
This doesn't look right compared to what other people are getting. I think my disk might be dodgy... :(

[IMG]http://img12.imageshack.us/img12/5130/screenshot20tbharddiska.png[/IMG]

---

### Post by andrewabc on 2011-06-02
> **ezzatron said:**
> This doesn't look right compared to what other people are getting. I think my disk might be dodgy... :(

I havn't seen a HDD do that before. Could be something wrong, or maybe something in background was running causing read speeds to be sporadic.

Maybe run test a couple times over a couple days and see if exact same result.

---

### Post by ezzatron on 2011-06-03
I ran the benchmark again a few times after a fresh reboot. Looks much healthier, but my green stuff looks a bit more sporadic than other people's. What does the green actually represent? Access time?

[IMG]http://img21.imageshack.us/img21/5130/screenshot20tbharddiska.png[/IMG][IMG]http://img38.imageshack.us/img38/5130/screenshot20tbharddiska.png[/IMG][IMG]http://img651.imageshack.us/img651/5130/screenshot20tbharddiska.png[/IMG]

---

### Post by Bandit on 2011-06-03
4x 320GB WD Blue Caviar 7200RPM 8MB Cache HDDs, Running RAID0 Stripe. 
These drives are about $45 USD each and super quiet. Best Size/performance/price setup you can go with if you have room for 4 HDDs.

---

### Post by NightwishFan on 2011-06-03
The second run you did seems normal to me.

---

### Post by Bandit on 2011-06-04
> **NightwishFan said:**
> The second run you did seems normal to me.

Yea much so. Must have had a few loose processes running a muck.




More users should post their results. I would really like to see some SSD -vs- RAID speeds going on here.

---

### Post by leviathan8 on 2011-06-04
[IMG]http://i.imgur.com/Auo8q.png[/IMG]

---

### Post by wolfen69 on 2011-06-04
> **Bandit said:**
> Running RAID0 Stripe. 
These drives are about $45 USD each and super quiet. Best Size/performance/price setup you can go with if you have room for 4 HDDs.

People still use RAID? Any time it takes 2 drives to get your stuff together, you're taking a big chance. 1 drive, and 1 backup drive is all it takes. Besides, aren't our computers fast enough as is?

---

### Post by Bandit on 2011-06-04
> **wolfen69 said:**
> People still use RAID? Any time it takes 2 drives to get your stuff together, you're taking a big chance. 1 drive, and 1 backup drive is all it takes. Besides, aren't our computers fast enough as is?

Actually most server do run RAID 1, 5, or 10.

Actually RAID is about redundancy and the ability to keep the system running even after a disc goes down. Mind you RAID0 isnt really RAID at all. Its just Disk Stripping. So there is nothing redundant about it. RAID 1 however is mirroring. So if you have two 320GB drives and one goes down. You never have to stop your system. You just replace the drive and it will rebuild the lost data on that drive. This is mainly used in small office servers were dependability is a higher priority then speed. There are a few more variations up to RAID5 which offers speed of a Stripped Array but the dependability of Mirroring found in RAID1. Requires a min of 3 disc also. RAID10 if I remember is similar but offers more speed if I can remember correctly. But its newer and may not be available on many older RAID cards.

But back to my Stripped setup. Yes MTBF is shot to crap. If regular MTBF is like 50,000 hours. I am suposed to divide that by 4 to figure how may hours I should be able to go without a problem. But I keep regular backups and Ubuntu only takes 10 to 20 mins to install and have desktop back to the way I had it. So its not that big of a deal to me. But no way would I run RAID0 on a server..


Cheers,
Exo

---

### Post by GWBouge on 2011-06-04
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822152054&cm_re=HD321KJ-_-22-152-054-_-Product]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152054&cm_re=HD321KJ-_-22-152-054-_-Product")
320GB SAMSUNG 7200rpm (came with this 3.5yr old XPS420)

Min Read: 18.1 MB/s
Max Read: 64.1 MB/s
Avg Read: 42.8 MB/s
Avg Acc: 16.2 ms

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822152245&Tpk=HD204UI]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152245&Tpk=HD204UI")
2TB SAMSUNG 5400rpm (eSATA media/backup drive)

Min Read: 64.7 MB/s
Max Read: 139.7 MB/s
Avg Read: 105.3 MB/s
Avg Acc: 16.8 ms

... my 5400rpm external spanked my 7200rpm OS drive.  Ha.

---

### Post by andrewabc on 2011-06-04
> **ezzatron said:**
> I ran the benchmark again a few times after a fresh reboot. Looks much healthier, but my green stuff looks a bit more sporadic than other people's. What does the green actually represent? Access time?


Yes it represents access time (see bottom right of benchmarks). With SSD the access time is MUCH smaller and more flat. One of many reasons SSD are much faster than hdd.

---

### Post by Paqman on 2011-06-04
> **TheeMahn2003 said:**
> I thought I would come back and post what I have learned with SSD's this is the first of many more I will purchase.  SSD's slow down over time, never to the speed of a regular Hard disk, but none the less they [slow down]("http://www.anandtech.com/show/2738"), a long read, the guy knows what he is talking about.  There is only one way to restore the speed and it is not re-installing Ubuntu, this will actually also slow it down.

Even a SSD with trim support will also slow down, yes [Trim support]("https://wiki.ubuntu.com/KernelTeam/Specs/KarmicSSD") is in Lucid


Can't say I'm concerned. I just retested my Intel X-25M and the average read is now 1% _faster_ than it was last May. 275.8MB/s with 0.1ms access time. I'd imagine that any drive with a decent controller (Intel, Indilinx, Sandforce, etc) and recent firmware with TRIM enabled should be more than capable of keeping itself in good shape.

---

### Post by Bandit on 2011-06-04
> **Paqman said:**
> Can't say I'm concerned. I just retested my Intel X-25M and the average read is now 1% _faster_ than it was last May. 275.8MB/s with 0.1ms access time. I'd imagine that any drive with a decent controller (Intel, Indilinx, Sandforce, etc) and recent firmware with TRIM enabled should be more than capable of keeping itself in good shape.

Hard part is finding good drives with TRIM support. So far AFAIK Ocz and Intel are the only ones that are really offering TRIM support. Which is a big thing if you run a RAID setup and dont want your data getting corrupted.

Access times on SSDs are fantastic, but so are 10,000RPM WD Raptor drives. I had a pair of older Raptors at one time. The avg access time I had was like 3.5ms. Which was very nice, but with age they got slower, or newer tech just got faster :-)  But access time wasnt a big deal for me, it was the over all speed when moving large files. Thats why I went the route of 4x 7200RPM drives. 4 of these drives together was just a tad faster then SSD, seek was slower but that was not a huge concern, drive space was also a factor. 

So it came down to a Ocz Agility2 180GB (R:285MBs/ W:275MBs) for $290 bucks. or..
4x WD Blue Caviars, 1.2TB (R:280MBs / W:270MBs) for $44x4 = $176 bucks..
(Under Win7 I get 380/370MBs speeds, not sure why Linux is a full 100MB slower)

I saved 120 dollars and gained 1TB of space.. 

[Plus it looks cool with 4 drives in my system]("https://picasaweb.google.com/exodist2009/MyPCNov2009#5604882071418563618") .. hehe :)

---

### Post by Paqman on 2011-06-05
> **Bandit said:**
> Hard part is finding good drives with TRIM support. So far AFAIK Ocz and Intel are the only ones that are really offering TRIM support. Which is a big thing if you run a RAID setup and dont want your data getting corrupted.


I think you'll find TRIM is better supported than that. The OCZ drives use the same controllers as most others AFAIK, and even if you were limited to Intel and OCZ then that's hardly a problem. Those are good drives, and come in a range of sizes and price/performance levels.

I wouldn't imagine many people are running RAID arrays of SSDs at home. SSDs are fast enough to not need RAID for speed, and are too expensive to use for serious data storage that would require the redundancy.

---

### Post by Bandit on 2011-06-05
> **Paqman said:**
> I think you'll find TRIM is better supported than that. The OCZ drives use the same controllers as most others AFAIK, and even if you were limited to Intel and OCZ then that's hardly a problem. Those are good drives, and come in a range of sizes and price/performance levels.

I wouldn't imagine many people are running RAID arrays of SSDs at home. SSDs are fast enough to not need RAID for speed, and are too expensive to use for serious data storage that would require the redundancy.

TRIM support is getting better. Thats why I think I mentioned newer drives. But older ones from a year or more ago were hurting from lack of TRIM support.

For home use with RAIDs and SSDs. Yea, I dont see many home users unless they are loaded with cache going RAID/SSD together. But the server market were my head is normally in, they are something to consider.

Here is something I really would like [OCZ REVODRIVE]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820227661"). Now thats speed, but surely need more space. It uses a RAID controller if I remember correctly to get the speed out also.

---

### Post by JustinR on 2011-06-05
I don't remember if I've posted in this thread, but I have a 40GB Intel X25-V.

Its usual read rate is 283MB/s with TRIM. TRIM is not enabled right now.

---

### Post by Khakilang on 2011-06-05
An old hard disk but still serve its purpose pretty well.

[ATTACH]194375[/ATTACH]

---

### Post by vehemoth on 2011-06-06
Full disk software raid1 of two 500gb WD drives (16mb cache, sata2 from memory)

---

### Post by BlendMe on 2011-06-27
So I just got these 2 drives today and thought I'd share my BM results.

I'm wondering though... what does the X-Axis represent? When I start partitioning the drive I want to put my main OS (11.04) in the higher performance area. Would that be the beginning or the end of the drive?

---

### Post by Ranko Kohime on 2011-06-27
:p

---

### Post by Bandit on 2011-06-27
> **Ranko Kohime said:**
> :p

LOL thats a hoot!

---

### Post by anirudh.srivathsa on 2011-06-28
what does the graph of a the read benchmark in ubuntu disk utility signify?
what are the significance of the three axes?
also i would like to know why i get a different graph for read benchmark every time i use read benchmark?

---

### Post by anirudh.srivathsa on 2011-06-28
Is write benchmark on a hard disk destructive?

---

### Post by NightwishFan on 2011-06-28
The write benchmark is destructive. I think it warns you first though.

---

### Post by BlendMe on 2011-06-28
Yeah it is destructive, but it won't run if the drive has a partition table.

---

### Post by anirudh.srivathsa on 2011-06-28
In what way is write benchmark destructive? what does it do to the hard disk? is the hard disk usable after that?

---

### Post by NightwishFan on 2011-06-28
It needs a blank disk to work. You can easily partition it afterwards. I would say if you have to ask you have no use for the benchmark. ;)

---

### Post by Ranko Kohime on 2011-06-28
> **Bandit said:**
> LOL thats a hoot!
Admittedly, it was a several-year-old USB disk to which I then proceeded to dd wipe from /dev/urandom...  which succeeded at 7.5KBps.  :|

The SSD and 1TB hard drive in my new laptop clocked ~280MBps and 98-41MBps (the same descending performance as other HDD's in this thread), respectively.

The SSD is an Intel 320-series 80GB.

The HDD is a WD Scorpio Blue 1TB, 5200 RPM.

---

### Post by markp1989 on 2011-06-29
Here is the result for my OCZ Revo Drive 

[https://dl.dropbox.com/s/dqg8rvetgwbu5jk/ssdbench.png](https://dl.dropbox.com/s/dqg8rvetgwbu5jk/ssdbench.png)

---

### Post by Bandit on 2011-06-30
> **markp1989 said:**
> Here is the result for my OCZ Revo Drive 

[https://dl.dropbox.com/s/dqg8rvetgwbu5jk/ssdbench.png](https://dl.dropbox.com/s/dqg8rvetgwbu5jk/ssdbench.png)

Haha... Thats what I want.. 

Which slot does yours use, the PCIX-4x one of 16x

---

### Post by Paradoxfox93 on 2011-07-18
Intel 320 40GB in Acer 5253-BZ602  Most benchmarks I've seen from google report 200-210MB/s.  hdparm gives 175MB/s  Aligned to 1MiB.  Natty Live  Gparted Automatically knew to align to 1MiB.  Finished with alt cd dm-crypt & LVM.  All basic SSD tweaks applied.  Still need to figure out what to do with /var it's killing me lol.  Anyway here it is.

Reads of 280MB/s pak and 260MB/s avg min 160MB/s I'm stoked.  Those are better rates than promised for the 80GB models so $*^% yeah!

Incidentally what do the green dots and gray blob of lines mean?

17s boot excluding cryptesetup entry.  Haven't built custom kernal yet wanted everything else in order. So that will speed it up a bit.

---

### Post by linuxman94 on 2011-07-18
Using a seagate 7200.12 on sata 2 (3.0 Gb/s) [http://www.newegg.com/Product/Product.aspx?Item=N82E16822148433]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148433") Latest firmware (CC49)

[IMG]http://dl.dropbox.com/u/7800678/2011-07-18_14-51-14.png[/IMG]

---

### Post by Antarctica32 on 2011-07-18
God, I probably have the worst here! lol, this is my best HDD, I found it in a junkyard last year on a P4.

---

### Post by wizard10000 on 2011-07-18
> **andrewabc said:**
> Anyone with a netbook with the default 160gb/250gb 5400rpm results?

Would be nice to know those. Also would be nice to know what happens when replaced with decent 30gb SSD. If it can speed up lots of or SATA or overhead doesn't allow full speed on netbook models.

I have a 60gb OCZ Agility 2 in my netbook - neither I nor a friend with a fast SSD in his netbook can get them over 125mb/sec.  The bottleneck appears to be the disk controller.

Both of us have partitions aligned properly, are using the noop scheduler and have noatime set in fstab.  The SSD is about 25% faster than the 500gb Samsung drive I used to have in the netbook and about half again as fast as the original 160gb hard drive.

---

### Post by andrewabc on 2011-07-18
> **Paradoxfox93 said:**
> Incidentally what do the green dots and gray blob of lines mean?

They are the access time which is shown on right side of graph, and bottom right of benchmark.

> **wizard10000 said:**
> I have a 60gb OCZ Agility 2 in my netbook - neither I nor a friend with a fast SSD in his netbook can get them over 125mb/sec.  The bottleneck appears to be the disk controller.

Both of us have partitions aligned properly, are using the noop scheduler and have noatime set in fstab.  The SSD is about 25% faster than the 500gb Samsung drive I used to have in the netbook and about half again as fast as the original 160gb hard drive.
Thanks for the info! Yes 125mb/s is SATAI limitation.
I wonder if the new AMD c-50 and e-350 processor/motherboard combo use SATAII? They are used in some netbooks etc.
EDIT:, apparently e-350 should have SATAIII (A50M chipset)
[http://en.wikipedia.org/wiki/Comparison_of_AMD_chipsets#Fusion_Controller_Hub_.28FCH.29](http://en.wikipedia.org/wiki/Comparison_of_AMD_chipsets#Fusion_Controller_Hub_.28FCH.29)

---

### Post by Paradoxfox93 on 2011-07-18
> **andrewabc said:**
> They are the access time which is shown on right side of graph, and bottom right of benchmark.


Thanks for the info! Yes 125mb/s is SATAI limitation.
I wonder if the new AMD c-50 and e-350 processor/motherboard combo use SATAII? They are used in some netbooks etc.
EDIT:, apparently e-350 should have SATAIII (A50M chipset)
[http://en.wikipedia.org/wiki/Comparison_of_AMD_chipsets#Fusion_Controller_Hub_.28FCH.29](http://en.wikipedia.org/wiki/Comparison_of_AMD_chipsets#Fusion_Controller_Hub_.28FCH.29)

Yes.  Mine is an E350 DDR3.  Sata II Dang it.  I knew i should have gotten that new plextor or Corsair SAtaII lmao.  Serves me right for bein' cheap eh.  I'm happy lol.

---

### Post by andrewabc on 2011-07-18
> **Paradoxfox93 said:**
> Yes.  Mine is an E350 DDR3.  Sata II Dang it.  I knew i should have gotten that new plextor or Corsair SAtaII lmao.  Serves me right for bein' cheap eh.  I'm happy lol.

EDIT: misread post
So you got a SATAII SSD and your laptop should be capable of SATAIII? SATAII SSD should be fast enough.

---

### Post by terrykiwi83 on 2011-07-18
Here is mine, must be on the slow side today.

120GB Kingston V-Series SSD - Its used for my Ubuntu System. I also have 2 x 1TB Drives & 1 x 2TB Drive but I will keep there performance hush hush.

[IMG]http://www.hi12.co.nz/shares/Screenshot.png[/IMG]

---

### Post by Paradoxfox93 on 2011-07-19
> **andrewabc said:**
> EDIT: misread post
So you got a SATAII SSD and your laptop should be capable of SATAIII? SATAII SSD should be fast enough.
It is. :guitar:  Truth be told I bought it for extended battery life more than speed. (From 4.5hrs->7hrs)

---

### Post by andrewabc on 2011-07-19
> **Paradoxfox93 said:**
> It is. :guitar:  Truth be told I bought it for extended battery life more than speed. (From 4.5hrs->7hrs)

That's nice. I'm really interested in e-350 netbook (if >=15.6" I'd want better processor, the new AMD 1.4ghz quad core). I'd want small screen no optical drive so it would be lighter (I have high end desktop for my number crunching/games).

How do you find the 1.6ghz dual core e-350 processor? Fast enough to do everything (web browsing I assume is done the most)? No problems playing videos (720/1080p?). Any multitasking slowdowns (launch lots of apps and processor can't handle it, I know SSD would be fast so does it make processor slowest part of laptop?)?

Was it easy to replace hdd to ssd? There was an easy access point for hdd/ram on bottom of laptop? Worst thing about some netbooks is that they don't have access to hdd and have to remove keyboard which makes them useless.

---

### Post by Paradoxfox93 on 2011-07-19
Direct access to RAM/HDD upgrade.  Three screws (Two for plate, one directly for disk mount, plate screws also secure disk mount), popped off the plate, secure fitting slides the HDD out to the side about an inch from a very secure and snug mounting.  Replace the bracket, fit the 320 perfectly slides back in snugly.  RAM is equally as easy with standard 204 SODIMM laptop mounts.  Two slots, comes with 1x2Gb chip so could hold up to 8Gb.

I bought performance RAM Gskill 1600mhz 9-9-9-28 (2x2GB).  Memtest86+ 4.20 (Natty is 4.10, you'll have to upgrade for any E350 proc to properly detect the RAM else it came up as DDR2 333mhz I almost flipped a wig lol).

Original RAM was 1066 7-7-7-20, as I had desired even though no BIOS options exist to configure the memory or processor (only time and boot order really) it automatically underclocked the RAM to 6-6-6-18 1066mhz.

The only other thing I looked at in the same range with a 12" 1215 family netbook with an E350, bluetooth, and USB3.  However, those are a pita to replace the hardware in require full disassembly.  There's also an MSI 13" in the same hardware family (bluetooth, USB3, E350, 4GB) but it's twice the price of this machine.  I agree.  DVD/CD drives are pretty much useless for something like this.  I wonder if I can replace the optical drive with another disk.

Video is great, flash was causing me problems but I'm sure that's an error of mine that should be fixed with this reinstall (I made /var partition to limit consumption per one article but that screwed my system six ways to sunday).  720/1080p no problem.  Fast enough certainly. I notice some slight lag opening some programs but nothing significant enough to make me wish I had a more powerful processor.  I think this is the *perfect* balance of power efficiency and delivery.

I played Sauerbraten for about an hour  with no problems ~40FPS average with med-high settings.  Multitask slowdown occured before I upgraded to 4Gb.  Doing so is pretty much a given with this piece especially if you get an SSD and don't use a swap like me.

Also, it has a full keyboard, numpad and all.  It's bigger than I thought but still only ~5lbs.  Wifi connects to AES-256 full speed-n (only within ~5 feet of router, lol 120-150 avg connection) proprietary and open source driver both work flawlessly.  Prop driver might get better rates but I haven't experimented enough to confirm that (probably just my head).

All hardware worked with Natty 64 out of the box on both bz602's I bought.  Only the SSD required any configuration and that's a given but as you see, runs flawlessly (even at 320 standard specs for the under preforming 40GB)

EDIT - I'm reinstalling so I've logged in from the laptop live before partitioning and run **write benches**.  Here are my further results.

---

### Post by andrewabc on 2011-07-19
Thanks for the write benchmark (note to others do not do it unless formatting!).

As long as the randoms are good a low write speed shouldn't be too bad unless for some reason you are always writing lots of data (but you shouldn't with only 40gb drive).

For basic tasks fast read sequential, and fast random read/write are important. Fast sequential write not as important, but still nice to have.

Thanks for all the info.

---

### Post by Paradoxfox93 on 2011-07-19
I might be wrong but I think sequential is irrelevant when speaking of SSD's.  Notice the seek time?  It's unnoticeable to change location for any sequence or lack thereof.  It's all the same.

I'll be posting some tutorials for encryption later on and another benchmark here in a minute.

I also recently discovered that you have to allocate space with Intel drives to support wear leveling.  Usually this might not be the case but I notice significant performance (and a ~5s shaving off my boot) after reinstalling this time.  Because I use LUKS/LVM FDE it treats more space as occupied it might seem.  This might seem to play an issue with wear leveling but it isn't if you leave it space to play with.  Doesn't need to be contiguous so you can stick a hidden partition in the middle of it too.  This is only true for Intel and other manufacturers whose controllers only pre-format off the wear leveling reserve and relegate control to the user.  Most advertise by the usable space and hide the space from the user.

Hence Intel's 40Gb vs. other's 32Gb.  Technically they're all 38GB.

Same, 64=76 

Which is the standard: Roughly %20

---

### Post by Bandit on 2011-07-19
Nice benchmark Paradoxfox93, I want to run a write benchmark. But not going to even think about attempting one unless I am going to reinstall everything that day. BTW, here is my current BM of 4x 320GB WD Blue Caviar 7200RPM Drives (1.3TB total) running RAID0. Not bad results for a $160 dollar setup.

---

### Post by Paradoxfox93 on 2011-07-19
So now that I've fixed my mistake with /var and partitioned off 8Gb for wear leveling I'm getting the promised (lower) rates of the 40GB model that I have.  Go figure.  One more time thought without LVM this time because I don't like what hdparm returns. Either it's LVM or it's the nature of using encryption which is an odd place to experience a slowdown.


To be honest it feels more responsive and smooth, though.  I'm going to do it one mroe time without LVM but before I do that I'm going to do it without any encryption to gather some benchmarks from that  for some comparison.  Gonna just back up my rc.local and fstab on my usb multiboot installer/diagnostic flash drive that makes all this a real breeze.  Stay tuned for updates, lol.

:~$ sudo hdparm -t /dev/LVMGROUP/VOLUME
[sudo] password for user: 

/dev/LVMGROUP/VOLUME:
 Timing buffered disk reads: 142 MB in  3.01 seconds =  47.24 MB/sec
:~$ sudo hdparm -t /dev/sda2

/dev/sda2:
 Timing buffered disk reads: 510 MB in  3.01 seconds = 169.62 MB/sec
:~$ sudo hdparm -t /dev/sda

/dev/sda:
 Timing buffered disk reads: 512 MB in  3.01 seconds = 170.32 MB/sec

---

### Post by Bandit on 2011-07-19
@ Paradox, 4 of those drives you got would be very nice stripped together. :)

---

### Post by Paradoxfox93 on 2011-07-19
If I were going for the highest preformance right now it'd be plextor's SATAIII for the 128mb DDR3 cache.

---

### Post by Hugh971 on 2011-07-19
Oh go on then, here's mine.

[IMG]http://i447.photobucket.com/albums/qq199/Hugh9191/nerdisms/Screenshot.jpg[/IMG]

---

### Post by Paradoxfox93 on 2011-07-19
On a no encryption install I'm getting 190MB/s from hdparm -t and reads from disk utility

0.1ms seeks vs. 2ms seeks and the original 280MB/s.  it appears encryption has an effect.  i wonder if it's a CPU/APU bottleneck?  Or the fact that some much less disk space is "free"

Boot is 21s =/  i wonder if all the new configs I added did that.  Used to be nothing from unlock to desktop.  12s to unlock.

---

### Post by Bandit on 2011-07-19
It looks accurate to me Paradox. 
Even running hdparm -t test on my raid array of 4 disc only show this:
> Timing buffered disk reads: 834 MB in  3.01 seconds = 277.49 MB/sec

SD Drives are not ultra speed demons, but they perform extremely well for a single disc meant for a system that doesn't have room for a huge raid array.
I.e; Laptops or computers with high vibration resistance needs.

---

### Post by brad1138 on 2011-08-26
[IMG]http://i544.photobucket.com/albums/hh359/brad3d/500sata.png[/IMG]

This seems quite low compared to the same drive in [post #26]("http://ubuntuforums.org/showpost.php?p=9254740&postcount=26")

Is there a bios setting I could have missed restricting the performance?

Brad

---

### Post by forliberty on 2011-09-12
Strangely, my drive performs faster in IDE mode than SATA mode. I have a Hitachi HDS721050CLA362 (7200 rpm, 500GB). It is a SATA 3.0 drive, with SATA connectors only. My mobo is Biostar TA880GB+ with AMD SB710. 

Running in "Native IDE" mode in the BIOS, I get: 
67.3 MB/s Min., 138.6 MB/s Max, Avg Read Rate: 110.1 MB/s, avg. access time 19.0 ms

Running in "AHCI" mode in BIOS, I get:
33.4 MB/s Min., 138.8 MB/s Max, Avg Read Rate: 108.8 MB/s, avg. access time 19.0 ms

Similar results with HDPARM. In IDE mode, I get:
1390.72 MB/sec for cached, 124.91 MB/sec buffered

In AHCI mode, I get:
1113.33 MB/sec for cached, 124.70 MB/sec buffered

I ran the tests several times, and always got a similar result, with SATA being slower than IDE. 

Any ideas????

---

### Post by NightwishFan on 2011-09-12
Numbers are very close and decent for a rotational drive.

---

### Post by lpwaqas on 2011-09-16
I have a very old WD drive, but its still running thats another thing I discovered unlike Seagate ****, WD drives run very very long; I had to change Seagate drives thrice in last two years but this old w.d. drive is still running and running :D

---

### Post by a2j on 2011-10-14
this is on ASUS Eee PC

---

### Post by a2j on 2011-11-03
and this is from my desktop, software RAID0 (4 WD black scorpios).

---

### Post by bohemian9485 on 2011-11-03
HP Pro 2000 Desktop 250GB SATA HDD 7200 RPM

---

### Post by Subliminal Aura on 2011-11-12
Agility 3 on a sata 2 controller - Dual core pentium laptop ICH8

[IMG]http://img402.imageshack.us/img402/6605/60gbsolidstatediskataoc.jpg[/IMG]

hdparm -t gives 210MB/s

However I'm concerned about those random access spikes and I'm not sure if the disk is aligned :/

fdisk -ul

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f2314

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   114655231    57326592   83  Linux
/dev/sda2       114655232   117231407     1288088   82  Linux swap / Solaris

---

### Post by Welly Wu on 2012-02-04
I have an ASUS N61JV-X2 notebook PC with Crucial 8 gigabytes of DDR3 1,066 MHz SDRAM and an Intel 2nd Generation 2.5" 34nm MLC NAND Flash X25-M 160 gigabyte Solid State Drive. I am getting these read benchmark results:

minimum read rate: 86.7 MB/s
maximum read rate: 206.8 MB/s
average read rate: 183.5 MB/s

I am using full disk encryption and I have a custom installation in which I use LUKS/LVM with AES-CBC mode 256 bits with SHA-256 hash algorithm. These read benchmark results look just about correct to me.

How do I run a read and write benchmark using Disk Utility?

---

### Post by Diabelica on 2012-09-12
Sony Vaio SVE1111M1EB netbook
60 GB Mach Xtreme SSD Sata 6 GB/s

minimum read rate: 364.7 MB/s
maximum read rate: 555.8 MB/s
average read rate: 530.3 MB/s

---

### Post by dli7319 on 2012-12-04
Kingston HyperX 120

---

### Post by Welly Wu on 2012-12-04
I hope that this works.

---

### Post by Welly Wu on 2012-12-04
As you can see, my System76 Lemur Ultra Thin (lemu4) notebook PC is much much faster than my previous ASUS N61JV-X2 notebook PC. It's a lot better too.

---

### Post by dli7319 on 2012-12-05
> **Welly Wu said:**
> As you can see, my System76 Lemur Ultra Thin (lemu4) notebook PC is much much faster than my previous ASUS N61JV-X2 notebook PC. It's a lot better too.

An ASUS N61JV-X2 isn't that bad to begin with

---

### Post by Subliminal Aura on 2012-12-05
> **Subliminal Aura said:**
> Agility 3 on a sata 2 controller - Dual core pentium laptop ICH8

[IMG]http://img402.imageshack.us/img402/6605/60gbsolidstatediskataoc.jpg[/IMG]


So whilst trying to squeeze more performance out of my already sweet laptop setup I managed to corrupt the partition so badly that grub didn't even recognise it, nor did any live cd

Please therefore accept my new benchmark with the super windows 8 operating system (same machine same spec)

[[IMG]http://img204.imageshack.us/img204/4025/attob.png[/IMG]](http://imageshack.us/photo/my-images/204/attob.png/)

Notice how the SSD hung at 16.0 ? :lolflag:

I better go and flash the firmware and see if the windoze driver likes it any better LOL

---

