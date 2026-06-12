---
title: "Tell us about your SSD experience."
date: 2010-10-21
forum: The Cafe
---

### Post by bartos on 2010-10-21
I just bought a Corsair Storage Solutions 60GB 2.5" Solid State Disk Drive Force Series.
I am very happy with it.
I did ```
sudo hdparm -t /dev/hda
```
and my results were 210 mb/s. The device is listed at 285 read speed.
It boots 10.10 in 10 seconds with the purple splash only showing for .5 second. Everything is snappy and opens very quick.

So what are your experiences with SSD's.

P.S. No STD stories.

---

### Post by earthpigg on 2010-10-21
from sudo lshw:

```
           *-disk:1
                description: ATA Disk
                product: OCZ-VERTEX
                ...
                size: 59GiB (64GB)
                ...
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   ...
                   size: 59GiB
                   capacity: 59GiB
                   ...
                   configuration: ... mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,

```


```
[chris: ~]$ sudo hdparm -t /dev/sdb1
[sudo] password for chris: 

/dev/sdb1:
 Timing buffered disk reads:  408 MB in  3.01 seconds = 135.36 MB/sec
```

this SSD is the root partition, and is about a year old. i haven't implemented any of the complex partitioning schemes folks recommend for SSDs, so it will be interesting to see the differences from folks that did do so.

---

### Post by drawkcab on 2010-10-21
pretty good.

---

### Post by JustinR on 2010-10-21
Hey,

I use an Intel SSD - 40GB.

[img]http://h1.ripway.com/mrreno/Benchmark_001.png[/img]

---

### Post by Untitled_No4 on 2010-10-22
I have an 80GB Intel X25-M drive. My experience with it is fast, quiet and cool.
The drive has my system on it (two partitions, root and home), it's using EXT4 and the only advice regarding SSD I've taken was not to have a swap partition, I'm too lazy for anything other than that.
Timing buffered disk reads:  748 MB in  3.00 secTiming buffered disk reads:  748 MB in  3.00 seconds = 249.28 MB/seconds = 249.28 MB/sec
```
sudo hdparm -t /dev/hda
Timing buffered disk reads:  748 MB in  3.00 seconds = 249.28 MB/sec
```

---

### Post by Foxcow on 2010-10-22
I have a 60 gig OCZ Agility2.  I wonder if my cpu is the bottleneck because from grub, my system boots into Ubuntu in ~20 seconds.  Other than that, I really like the performance of the drive.

---

### Post by the8thstar on 2010-10-22
Hey guys,

I'm going to use this thread to ask you this: since I'm using a Core Solo laptop right now, will a change of HDD to an SSD make a lot of difference or will the CPU speed eventually be the limiting factor (1.86GHz, 2Gb RAM)?

Thanks for your feedback.

---

### Post by johntaylor1887 on 2010-10-22
> **Untitled_No4 said:**
> it's using EXT4

I was under the impression that ext2 was the preferred file system on SSD's.

---

### Post by Untitled_No4 on 2010-10-22
> **johntaylor1887 said:**
> I was under the impression that ext2 was the preferred file system on SSD's.

I read that somewhere. Then again, I read somewhere else that ext4 was just as good nowadays. I don't know, I'll never know and therefore I decided to use my SSD as I would use any other Hard Drive (sans Swap). It's not that I want it to fail, but I figured out that by the time it does SSDs will be better and more affordable anyway, and I'll just replace mine (yes, I do backup religiously, but I always have).

---

### Post by oregonbob on 2010-10-22
I am curious what else you notice besides fast bootups and impressive speeds when you do diagnostics. Does it make a big difference in apps you use, etc?

---

### Post by Paqman on 2010-10-22
> **the8thstar said:**
> 
I'm going to use this thread to ask you this: since I'm using a Core Solo laptop right now, will a change of HDD to an SSD make a lot of difference or will the CPU speed eventually be the limiting factor (1.86GHz, 2Gb RAM)?


Yes and no.

Some tasks are very CPU dependant. For those, yes, your CPU will be the bottleneck. But for any heavily I/O dependant task, switching to an SSD will show large benefits, regardless of your CPU speed. Magnetic drives are a massive bottleneck even on computers with a very fast CPU/RAM/mobo. Things which are heavy on I/O will be things like booting and opening apps that haven't been pre-cached.

> **johntaylor1887 said:**
> I was under the impression that ext2 was the preferred file system on SSD's.

Only if you're paranoid, or have a very early-model SSD that doesn't have effective wear-levelling. The only reason to use EXT2 is that it does marginally less writes to disk. If your drive doesn't do wear levelling (early SSDs, Compact Flash and SD cards, etc) then cutting down on writes would improve reliability. On a recent 2.5" SSD however, reliability isn't an issue, and you're better off using EXT3 or 4 for the extra performance.

---

### Post by andrewabc on 2010-10-22
> **Foxcow said:**
> I have a 60 gig OCZ Agility2.  I wonder if my cpu is the bottleneck because from grub, my system boots into Ubuntu in ~20 seconds.  Other than that, I really like the performance of the drive.

You'd have to show us your bootchart, and also system->admin->disk utility->read benchmark

You have Athlon 64 x2 6000+, that is dual core correct?
Your CPU should have nothing to do with bottleneck. I get from grub to desktop in a couple seconds using 60gb vertex which is same as your agility using core2duo 1.8ghz.

Based upon your signature, you have laptop? laptop limited to SATAI speeds. So you are getting 120mb/s read. If you had desktop it would be ~200mb/s

> **the8thstar said:**
> Hey guys,

I'm going to use this thread to ask you this: since I'm using a Core Solo laptop right now, will a change of HDD to an SSD make a lot of difference or will the CPU speed eventually be the limiting factor (1.86GHz, 2Gb RAM)?

Thanks for your feedback.

Your CPU won't be much of a bottleneck (to access data/apps), but it will impact performance.
You are on laptop which is limted to SATAI. So you will get 120mb/s max read.

Show us output of system->admin->disk utility->read benchmark and it will show your read speed from hdd. You will get 120mb/s almost constant from ssd. ssd will be faster but as to whether worth the price is the question.

> **oregonbob said:**
> I am curious what else you notice besides fast bootups and impressive speeds when you do diagnostics. Does it make a big difference in apps you use, etc?

Yes and no. Firefox is much faster, especially when typing in addressbar due to the fact that it is 25mb sqlite database which brought my desktop hdd to a crawl. Lots of random write/read with firefox which ssd help with alot. For other apps there is a small increase in speed. Not enough to go "Wow!", but enough that if you went and opened a lot of apps at once or multitasking with stuff that access data from ssd, then yes you will see improvements especially since if on desktop getting 200mb/s read vs <100mb/s on hdd.

As for ext2 vs ext4, it doesn't matter much unless you are paranoid about speed and longevity. I use ext4 on both my computers that have SSD. It's not something to be overly worried about.

Just use SSD for OS+apps and everyday used small files. Keep your media and backups on hdd.

---

### Post by Foxcow on 2010-10-22
> **andrewabc said:**
> You'd have to show us your bootchart, and also system->admin->disk utility->read benchmark

You have Athlon 64 x2 6000+, that is dual core correct?
Your CPU should have nothing to do with bottleneck. I get from grub to desktop in a couple seconds using 60gb vertex which is same as your agility using core2duo 1.8ghz.

Based upon your signature, you have laptop? laptop limited to SATAI speeds. So you are getting 120mb/s read. If you had desktop it would be ~200mb/s

Your CPU won't be much of a bottleneck (to access data/apps), but it will impact performance.
You are on laptop which is limted to SATAI. So you will get 120mb/s max read.

Show us output of system->admin->disk utility->read benchmark and it will show your read speed from hdd. You will get 120mb/s almost constant from ssd. ssd will be faster but as to whether worth the price is the question.



Yup 6000+ is a dual core chip and those are the specs for my desktop. :)

[IMG]http://i208.photobucket.com/albums/bb252/Foxcow/test.png[/IMG]

---

### Post by jdong on 2010-10-22
> **johntaylor1887 said:**
> I was under the impression that ext2 was the preferred file system on SSD's.

That's a bad idea, unless you can guarantee you'll never have an improper shutdown. Otherwise, your SSD is just as vulnerable as a rotational HDD to filesystem corruption and the need to run a lengthy filesystem check on the next reboot.

---

### Post by amp711 on 2010-10-22
80Gb Intel SSD in my machine.  Fast as all get out and have had no reliability issues.

No metrics available at work, but I'll try and throw something up tonight..

---

### Post by andrewabc on 2010-10-22
> **Foxcow said:**
> Yup 6000+ is a dual core chip and those are the specs for my desktop. :)

Ok, you got agility2, and seems to be running at full SATAII speeds.
So it should definitely not take 20 seconds to get to desktop from grub.

I'm guessing something is doing something when loading and your system waits for it to complete before continuing. Bootchart should show this.

---

### Post by Foxcow on 2010-10-22
> **andrewabc said:**
> Ok, you got agility2, and seems to be running at full SATAII speeds.
So it should definitely not take 20 seconds to get to desktop from grub.

I'm guessing something is doing something when loading and your system waits for it to complete before continuing. Bootchart should show this.


Sorry about that, I completely forgot to run that.  Its incoming shortly...

---

### Post by Foxcow on 2010-10-22
Here we are:

[IMG]http://i208.photobucket.com/albums/bb252/Foxcow/bigtop-maverick-20101022-1.png[/IMG]

---

### Post by andrewabc on 2010-10-22
According to bootchart I don't see anything wrong.
10 seconds is normal (they change bootchart settings with every ubuntu release, so hard to keep track of).

You sure it is 20 seconds from grub->desktop?

Here's mine.

[[IMG]http://img529.imageshack.us/img529/3103/andrewdesktopmaverick20.th.png[/IMG]](http://img529.imageshack.us/i/andrewdesktopmaverick20.png/)

I timed from grub->desktop and it was 9-10 seconds. So about same as my bootchart.

---

### Post by Foxcow on 2010-10-22
> **andrewabc said:**
> According to bootchart I don't see anything wrong.
10 seconds is normal (they change bootchart settings with every ubuntu release, so hard to keep track of).

You sure it is 20 seconds from grub->desktop?

Here's mine.

[[IMG]http://img529.imageshack.us/img529/3103/andrewdesktopmaverick20.th.png[/IMG]](http://img529.imageshack.us/i/andrewdesktopmaverick20.png/)

I timed from grub->desktop and it was 9-10 seconds. So about same as my bootchart.




I'll have to time it again when I get home but it was ~20 seconds to desktop.  It was actually 23 seconds but I took three seconds off so I could type my password and press enter.

---

### Post by Windows Nerd on 2010-10-22
> **Foxcow said:**
> I have a 60 gig OCZ Agility2.  I wonder if my cpu is the bottleneck because from grub, my system boots into Ubuntu in ~20 seconds.  Other than that, I really like the performance of the drive.

The cpu is likely the bottleneck. I am in the same situation: I have a Kingston V-series SSD and a Pentium 4. Day-to-day activities are blazing fast, but I still get a 17 second boot

---

### Post by andrewabc on 2010-10-22
> **Foxcow said:**
> I'll have to time it again when I get home but it was ~20 seconds to desktop.  It was actually 23 seconds but I took three seconds off so I could type my password and press enter.

Maybe that is the difference. I auto login. Try auto login and see if it makes a difference. :)

> **Windows Nerd said:**
> The cpu is likely the bottleneck. I am in the same situation: I have a Kingston V-series SSD and a Pentium 4. Day-to-day activities are blazing fast, but I still get a 17 second boot
As far as I can tell his CPU is faster than mine (my dual core 1.8ghz vs his dual core 3ghz at least that is what wikipedia is telling me), so I don't see how that is the reason in his case. I also think his motherboard/graphics is better than my 'cheap' store bought computer.

---

### Post by Foxcow on 2010-10-23
> **andrewabc said:**
> Maybe that is the difference. I auto login. Try auto login and see if it makes a difference. :)





A very good suggestion!  Time to desktop from Grub is ~15 seconds.  still not as fast as other claims but fast indeed.  I will do some more research.

---

### Post by weasel fierce on 2010-10-23
I've been pondering a SSD drive for a while now.

The main concern has traditionally been how long they last, but I haven't looked into the technology much in the past few months. Any thoughts or experiences?

---

### Post by johntaylor1887 on 2010-10-23
> **weasel fierce said:**
> I've been pondering a SSD drive for a while now.

The main concern has traditionally been how long they last, but I haven't looked into the technology much in the past few months. Any thoughts or experiences?

From what I've heard, if you were writing to the drive 24/7, it would take 3 years before it would wear out. In other words, I wouldn't worry about it.

Btw, does anyone know of a definitive guide/how-to for SSD's in linux?

---

### Post by efflandt on 2010-10-29
> **the8thstar said:**
> since I'm using a Core Solo laptop right now, will a change of HDD to an SSD make a lot of difference or will the CPU speed eventually be the limiting factor (1.86GHz, 2Gb RAM)?

I just bought an Intel X25-M 80 GB that I intend(ed) to install in my desktop (once I figure out if I have proper connectors).  But using my laptop to install Maverick on it in the mean time made me realize how slow my laptop drive was.

My laptop is a a Toshiba A105 from 2006 with 1 GB RAM that says Centrino Duo (dual core 1.66 MHz).  My 160 GB hard drive is only 4200 RPM and not any faster than a USB 2.0 external drive (~31 MB/sec for hdparm -t).  The SSD is > 120 MB/s for hdparm -t (limited by SATA I of the laptop).  So it is 4 times faster reading, and totally quiet, unless the laptop is busy enough to run its fan.  Since it is the only OS, it skips grub menu and is 11 sec from BIOS password to GUI login, then 6 sec to desktop.

The Intel SSD is capable of reading twice that fast with SATA II.  My desktop PC is capable of SATA II, but its hard drive does 117 MB/sec hdparm -t.  So disk reads on my old laptop with SSD are faster than the hard drive in my new desktop PC with i5 650 3.2 GHz and 8 GB RAM.

PS: I just installed the SSD in my desktop, and instead of 120 MB/sec it did on my laptop:

/dev/sdb:
 Timing buffered disk reads:  752 MB in  3.00 seconds = 250.56 MB/sec

---

### Post by futz on 2010-10-29
My boot drive is a 128GB G.Skill Falcon II Indilinx w/64MB buffer. I absolutely LOVE it.

Boot times are fast, but even better is that program load times are nonexistent. Almost everything loads virtually instantly, even porky Firefox. :) Drive checks go by so fast you usually don't even see them. Update installs are super fast (you still have to wait a little for the download). On this machine the CPU is never the bottleneck, so adding a SSD just makes it SO nice and snappy quick.

```
futz@shiny:~$ sudo hdparm -t /dev/sdd1

/dev/sdd1:
 Timing buffered disk reads:  636 MB in  3.00 seconds = 211.94 MB/sec

```

---

### Post by ubunterooster on 2010-10-29
I have a PCI SSD with a 1100MBps read and 780MBps write. I use it to have 33GB swap so no matter what I am doing (I can be doing odd stuff) I won't run out of RAM. 

  I really like mine

---

### Post by Stan_1936 on 2010-10-29
> **bartos said:**
> ...2.5" Solid State Disk Drive...
So what are your experiences with SSD's...

OCZ Vertex 30 GB

Great with Windows

AWFUL(and NOT recommended) with Ubuntu 10.04 or higher. With Ubuntu, it has proven to be nothing more than a waste of my time. I will not risk trying it again.

No I do not wish to get into further details.

---

### Post by annoyingrob on 2010-10-29
I'm seriously considering buying one of those hybrid drives for my laptop (500GB magnetic with 4GB SSD). The local computer place has them on sale for 100 bucks.

---

### Post by futz on 2010-10-30
> **annoyingrob said:**
> I'm seriously considering buying one of those hybrid drives for my laptop (500GB magnetic with 4GB SSD). The local computer place has them on sale for 100 bucks.
If you weren't running a lappy you could also use a [Silverstone HDDBoost]("http://www.silverstonetek.com/products/p_contents.php?pno=HDDBOOST"). The go for about [$55 around here]("http://ncix.com/products/?sku=51338&vpn=RL-HDDBOOST&manufacture=Silverstone%20Technology"). Add one to any drive without reinstalling your OS or changing any files on the drive and voila! Now that drive has a 30GB or 60GB or however big you can afford cache. Works pretty well. I have one in my Windoze gaming box (1 Terabyte drive) with a 60GB SSD on it. Buddy of mine has one too and he's been happy with its performance as well.

---

### Post by mr-woof on 2010-10-30
wow, some of your drives are seriously quick according to Hdparm. The only ssd drives I have are in my little netbook (16gb and 4gb) :)

90mb in 3.03 seconds = 29.65mb and 50mb in 3.14 seconds = 15.93!

Ran the program on my three sata drives in my main machine as a comparison and they got anywhere between 170mb - 250mb.

I think I might invest in a new ssd, I wonder if they can be replaced in a eee900? lol

---

### Post by MooPi on 2010-10-30
I've got some seriously disappointing numbers from mine. 
```
dev/sda2:
 Timing buffered disk reads:  298 MB in  3.01 seconds =  98.84 MB/sec
```OCZ 120Mb Vertex drive
These represent an ntfs file system and may be the reason for the slow time. Anyone know if this test performs bad on ntfs file structure and does the test do better on native Linux systems ?

---

### Post by markp1989 on 2010-10-30
hdparm for my series 1 OCZ vertex 32gb in my htpc 

> mark@torrentslave:~$ sudo hdparm -t /dev/sda

/dev/sda:
 Timing buffered disk reads:  410 MB in  3.00 seconds = 136.52 MB/sec
mark@torrentslave:~$



and the picture is my 64gb super talent ssd

---

### Post by switch10 on 2010-10-30
I have one of those mini PCI SSD's in my Dell mini 9.  The speed on those things are pretty disappointing.  Approximately 60 MB/sec.

---

### Post by andrewabc on 2010-10-30
> **ubunterooster said:**
> I have a PCI SSD with a 1100MBps read and 780MBps write. I use it to have 33GB swap so no matter what I am doing (I can be doing odd stuff) I won't run out of RAM. 

  I really like mine

Is it possible for you to do a system->admin->disk utility->read speed benchmark on the device and post it here? How large (gb) is it?


> **Stan_1936 said:**
> OCZ Vertex 30 GB

Great with Windows

AWFUL(and NOT recommended) with Ubuntu 10.04 or higher. With Ubuntu, it has proven to be nothing more than a waste of my time. I will not risk trying it again.

No I do not wish to get into further details.

Well, can you at least say if drive failed (some do, no different than hdd), or if ubuntu just not work well with it?

I got 2 60gb vertex1 and no problems yet and worked with 9.10, 10.04, 10.10 on 2 different computers. You have latest firmware (1.6)?

> **annoyingrob said:**
> I'm seriously considering buying one of those hybrid drives for my laptop (500GB magnetic with 4GB SSD). The local computer place has them on sale for 100 bucks.
I don't really recommend those. If you have access to an external hdd, then just put in a regular SSD, and when at home keep data on hdd.
The hybrids are still slower than normal SSD. but your laptop is most likely limited to SATAI, so not sure on what is best.

> I think I might invest in a new ssd, I wonder if they can be replaced in a eee900? lol
Don't bother. The older eee I think used pci something or other and SSD for them are crap.

---

### Post by ubunterooster on 2010-10-30
> **andrewabc said:**
> Is it possible for you to do a system->admin->disk utility->read speed benchmark on the device and post it here? How large (gb) is it?
256GB. That is the average resulting read from disk utility.

---

### Post by brian3 on 2010-10-31
just bought a kingston 64gb ssd hard drive,amazing performance increase in boot 14 sec.
 done test on harddrive 
benchmark; Max 257.3
    :      average:248.3
            acess 0.3ms
found some trimm software if anybody is interested Disk Trim at sourge force does everything for you,trims your drive memory every 4 days (auto)
brian 3

---

### Post by andrewabc on 2010-10-31
> **brian3 said:**
> just bought a kingston 64gb ssd hard drive,amazing performance increase in boot 14 sec.
 done test on harddrive 
benchmark; Max 257.3
    :      average:248.3
            acess 0.3ms
found some trimm software if anybody is interested Disk Trim at sourge force does everything for you,trims your drive memory every 4 days (auto)
brian 3

If running 10.10, it can do TRIM if you enable (add) it in fstab. Although it would only activate when you empty trash (So I hear).

---

### Post by MooPi on 2010-10-31
Thank goodness I just retested my SSD while using Windows 7 instead of Linux. The Windows utility was able to correctly gauge the speed of the drive. Read times averaged 230 Mb/sec and write speed averaged 200 Mb/sec. I don't have to trash my SSD now :P

---

### Post by lolobu on 2010-11-01
I've just installed Maverick on an OCZ Vertex2 60Go. The result is awesome. My PC boots in 7s (not counting BIOS start-up) and everything is much faster than before.
You don't need to worry about all those alignment issues with Maverick since the partitioner during the install process automatically aligns the partitions properly (with either automatic or manual partitioning).
I just put /tmp in a tmpfs and /var/log on another partition on a classic HD to reduce the number of writings and added discard (to enable TRIM) and noatime (no read access date update) in the fstab for the same reason.

---

### Post by ubunterooster on 2010-11-01
I thought very few drives had TRIM support?

LOL, mine has it done OS independently

---

### Post by lolobu on 2010-11-01
Well, most recent SSD do have TRIM support now.
I'm not an expert but my understanding is that TRIM on an SSD cannot be OS indenpendant. I've read quite a bit on the subject and with Ubuntu, you have to have an ext4 partition, a kernel >=2.6.33 and the partition mounted with the discard option in the fstab to enable on the fly TRIM. Check:
[http://ubuntuforums.org/showthread.php?t=1463870]("http://ubuntuforums.org/showthread.php?t=1463870&highlight=ssd+lucid")
[http://ubuntuforums.org/showthread.php?t=1596214]("http://ubuntuforums.org/showthread.php?t=1596214&highlight=ssd+lucid")

---

### Post by ubunterooster on 2010-11-01
> **lolobu said:**
> I'm not an expert but my understanding is that TRIM on an SSD cannot be OS independent.[]("http://ubuntuforums.org/showthread.php?t=1596214&highlight=ssd+lucid")I use a PCIe SSD that has its own OS built into the drive that has to boot before I can boot my OS. That and the four indilux controllers (yes, four) make it a very quirky type of drive. That Built-in OS really slows the boot process, but once booted, it is blistering fast. I have seen others wonder if the built-in OS made for a security vulnerability but I have not found evidence to support that.

---

### Post by andrewabc on 2010-11-01
> **ubunterooster said:**
> I thought very few drives had TRIM support?

LOL, mine has it done OS independently

Anything second generation with updated firmware can do TRIM. The only stuff that wouldn't would be the crap SSD from 2008 and before. TRIM doesn't work in RAID either.

Indilinx (2009), Intel (November 2009), probably the newer jmicron drives from 2009. And anything in 2010 would have TRIM. Most sellers have updated firmware available.

---

### Post by xinel on 2010-11-11
All drives are encrypted with twofish 256 dmcrypt

ssd OCZ vertex 2 60GB
fstab has defaults,noatime,discard
is /
sudo hdparm -t /dev/sdd
/dev/sdd:
Timing buffered disk reads:  472 MB in  3.01 seconds = 157.02 MB/sec

sata2 WD20EADS Green 2TB
/dev/sda:
Timing buffered disk reads:  304 MB in  3.01 seconds = 101.01 MB/sec

sata3 WD1002FEAX 1TB
/dev/sdb:
Timing buffered disk reads:  386 MB in  3.01 seconds = 128.18 MB/sec

sata3 WD1002FEAX 1TB
/dev/sdc:
 Timing buffered disk reads:  372 MB in  3.01 seconds = 123.75 MB/sec

---

### Post by obbe on 2010-11-19
hi, sorry but I got a little bit confused by the previous posts, I've got a OCZ SSD 120GB Vertex 2 and I want to install ubuntu 10.10 on it, so will I have to enable TRIM or do something to increase the performance, or using a ext4 filesystem is enough? Thanks

edit: Thanks lolobu ;)

---

### Post by lolobu on 2010-11-19
Install Ubuntu 10.10 with an ext4 file system. Once the installation is done, open the file /etc/fstab (with sudo to be able to write in it).
You should have one line that look like that (UUID value will be different of course):
```
UUID=4b342141-ef31-43fb-b450-e43044f158f1 /               ext4    errors=remount-ro 0       1

```
Just add discard and noatime like that:
```
UUID=4b342141-ef31-43fb-b450-e43044f158f1 /               ext4    discard,noatime,errors=remount-ro 0       1
```

With that, you'll have TRIM support

---

### Post by jdong on 2010-11-20
I'd suggest using relatime instead of noatime -- some applications rely on access times being updated.

But the relevant option to enable TRIM is discard.

---

### Post by hugmenot on 2010-11-21
I found a rogue Samsung firmware flasher with TRIM support online that managed to flash my Lenovo Thinkpad SSD via hotplugging and a DOS boot disk.

After flashing and before copying the data back:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=176203&stc=1&d=1290373941[/IMG]

After rsyncing the system back from backup:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=176202&stc=1&d=1290373743[/IMG]

Anyone have an explanation for the discrepancy in read speed? Is there some kind of compression in place that makes reading zeroes faster? (The upper 25% are all free space I assume)

---

### Post by Anubis on 2010-12-23
> **ubunterooster said:**
> 33GB swap so no matter what I am doing (I can be doing odd stuff) I won't run out of RAM.

A 33gb swap!!!?!! Outrageous!

---

### Post by Anubis on 2010-12-23
> **Stan_1936 said:**
> OCZ Vertex 30 GB

Great with Windows

AWFUL(and NOT recommended) with Ubuntu 10.04 or higher. With Ubuntu, it has proven to be nothing more than a waste of my time. I will not risk trying it again.

No I do not wish to get into further details.

Outrageous!

---

### Post by Anubis on 2010-12-23
> **MooPi said:**
> Thank goodness I just retested my SSD while using Windows 7 instead of Linux. The Windows utility was able to correctly gauge the speed of the drive. Read times averaged 230 Mb/sec and write speed averaged 200 Mb/sec. I don't have to trash my SSD now :P

Hilarious!

---

### Post by Anubis on 2010-12-23
> **lolobu said:**
> I've just installed Maverick on an OCZ Vertex2 60Go. The result is awesome. My PC boots in 7s (not counting BIOS start-up) and everything is much faster than before.
You don't need to worry about all those alignment issues with Maverick since the partitioner during the install process automatically aligns the partitions properly (with either automatic or manual partitioning).
I just put /tmp in a tmpfs and /var/log on another partition on a classic HD to reduce the number of writings and added discard (to enable TRIM) and noatime (no read access date update) in the fstab for the same reason.

Bingo! I have the same drive and did the exact same things. I was getting 275 read 250 writes. But as I kept benchmarking BEFORE I READ THE OCZ FORUMS on NOT to do repetitive benchmarking without at least letting the drive maintain itself over the course of a few weeks before testing again.

---

### Post by Anubis on 2010-12-23
> **xinel said:**
> All drives are encrypted with twofish 256 dmcrypt

ssd OCZ vertex 2 60GB
fstab has defaults,noatime,discard
is /
sudo hdparm -t /dev/sdd
/dev/sdd:
Timing buffered disk reads:  472 MB in  3.01 seconds = 157.02 MB/sec

sata2 WD20EADS Green 2TB
/dev/sda:
Timing buffered disk reads:  304 MB in  3.01 seconds = 101.01 MB/sec

sata3 WD1002FEAX 1TB
/dev/sdb:
Timing buffered disk reads:  386 MB in  3.01 seconds = 128.18 MB/sec

sata3 WD1002FEAX 1TB
/dev/sdc:
 Timing buffered disk reads:  372 MB in  3.01 seconds = 123.75 MB/sec

We need to know what kind of machine you have? Those Vertex2 speeds are 100mb/s off!

---

### Post by Legendary_Bibo on 2010-12-23
My laptop boots in around a minute, does having several programs start on start up affect boot times? I mean I have compiz, cairo-dock, empathy, gnomenu, and some desktop widgets. Does that slow down boot up times?

---

### Post by ubunterooster on 2010-12-24
> **Anubis said:**
> A 33gb swap!!!?!! Outrageous!
Try running a city of virtual machines on just regular RAM

---

### Post by Foxcow on 2011-05-08
How is everyone doing with 11.04?  Boot times in particular.

---

### Post by mr-woof on 2012-06-25
Hi all,

sorry to drag this thread back up, but I'm need of a Ubuntu Forums favour :)

In this PC at the moment, I have three drives. An old 80gb, 500gb and my new 1tb (about a year old), I ran sudo hdparm -t on all three with the following results:

Sda - 1tb - 388 MB in  3.01 seconds = 128.78 MB/sec
Sdb - 80gb - 210 MB in  3.01 seconds =  69.77 MB/sec
sdc - 500gb - 270 MB in  3.01 seconds =  89.69 MB/sec

We have Dell Optiplex 790's in work with SSD's in them, I booted crunchbang from usb live cd and ran the hdparm command on the ssd and it came back with 475 mb/sec.

Now, does anyone have a OCZ 60GB Agility 3 ssd? If yes, can you run the hdparm command please? 

Everyone else, what speeds are you getting from your newer drives?

I'm very tempted to purchase a ssd for this new machine, I want some proof in the hdparm speeds that I'm going to see a big difference.

Thanks all, can't wait to see the results. I can almost hear my credit card crying in pain.

---

