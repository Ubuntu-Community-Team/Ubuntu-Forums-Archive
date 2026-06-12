---
title: "Flash disk vs hard disk?"
date: 2008-02-15
forum: The Cafe
---

### Post by Sunnz on 2008-02-15
Hi, just wondering what are the different of read and write speed between a USB Flash disk and a typical internal SATA hard disk at 7200-10000 rpm?

Flash device has limited number of writes, but if one were to install only the kernel and programs, like /boot, /usr on the USB Flash disk and leave them as read only, and just rest of the system on the internal disk, would there be any performance gain? Or would the Flash disk be bottlenecked by the USB bus?

Thanks.

---

### Post by BlueKoala on 2008-02-15
In all honesty, I would not recommend a USB flash drive for conventionnal purposes due to the USB bus speed. That would translate into a maximum of 60MBps whereas the practical throughput it acutally closer to 50MBps. That is if the flash memory can read that fast. There are HDD's out there now that have an average read rate of ~74MBps for close to or under 200$ (WD750GBs SATA II). I/O operations also come to mind.

I'm speculating that with a USB key it would take up to 5 times as long to boot an OS, although I could be wrong.

The limited amount of re-writes should not be of concern unless you're planning on using it as swap space.
Although if you wish to create a portable OS, a USB key would definetly not be a bad choice, but for any conventionnal use, a HDD is your best bet.

Although if you're using a laptop, a SSD (Solid state drive) is a good option, if of course you have the funds for it.

What were you planning to use it for anyway?

---

### Post by Sunnz on 2008-02-15
I am going to set up a router using a small old machine that I would pretty much just set it up and just leave it in the closet and forget it... that's why I am even considering some kind of "alternate" storage in the first place, I don't exactly need a lot of spaces inside and probably never going to write anything on it once it is set up.

I have done a little more research... while Sata II supports up to 300 Gbit/s, hard drive of around 7200 - 10000 rpm is around 1.0 to 1.6 Gbit/s... that however is still faster then USB2.0's theoretical maximum throughput of 0.480 Gbit/s.

On the other side, Flash drives has no seek time, so random access to memory is much faster than a hard disk... it is just the transfer rate that is slower.

So flash would 'win' in situation where access to a lot of little parts as opposed to access to a few big chuck of data.

So... I guess the question would become which one would benefit the OS performance under what condition?

P.S. regarding boot up time I would just try a minimal installation of an OS and see which one boots up faster.

---

### Post by regomodo on 2008-02-15
for what you need, flash will do. As long as the i/o rate is low, you have no swap, flash will be fine. It'll be silent, use little power and space. BTW, there is a seek time ~0.1ms (if i remember correctly) for sequential  and random reads.

What do you intend on doing with this?

I wonder how soon somebody will say "but flash wears out!". Don't.

---

### Post by Sunnz on 2008-02-16
What do I intend to do with this? Well, use it as an internet gateway... like you know, it has a wireless access point and computers can connect to it and use the net.

---

### Post by LaRoza on 2008-02-16
The programs will be loaded into RAM, which is much faster than SATA or USB.

Depending on the OS on it, you might be able to load it all into RAM anyway.

---

### Post by gn2 on 2008-02-16
If it's for connecting other computers to for internet access, why not just use a router?

It will be cheaper and greener.

---

### Post by ssam on 2008-02-16
also no disk ever saturates the interface speed. i get 70-80 MB/s with a WD Raptor on SATA. and around 65 MB/s with a Deskstar T7K250 also on SATA. i get 16 MB/s with a cheap 1GB usb key. 7 MB/s with a 50x Compactflash in a USB reader. (wikipedia says that CF speed based on 1x being 150KB/s so 50x = 7.5MB/s. There are 300x cards on the market which gives 45MB/s).

those numbers are from running
```
sudo hdparm -t /dev/sdX
```
a few times.

samsung claim 100MB/s on their IDE solid state drives.

of course seek time is also very important for boot speed.

don't worry about limited writes. profesional photographers will fill up flash cards and delete the files every day, and the cards still last for years. for things like /usr /etc /lib and similar you will have no problems. even for a home folder it might be ok. lots of flash memory has very long warranty periods.

---

### Post by az on 2008-02-16
> **BlueKoala said:**
> 
The limited amount of re-writes should not be of concern unless you're planning on using it as swap space.

That's not true.  You could read/write to the drive continuously for something like fifty years before you reach the write-limit.  

A flash drive continuously cycles through the available cells to prevent writing to the same cell twice in a row. 

> **Sunnz said:**
> 

On the other side, Flash drives has no seek time, so random access to memory is much faster than a hard disk... it is just the transfer rate that is slower.


Actually, there is quite a lot of overhead.  Performance between different devices will vary depending on the controller chip that abstracts the actual memory cells from the block device.  You really need to run an i/o benchmark.

If you're just going to use this as a router, you will be fine.  Most routers on the market use really slow processors anyway (like less than 100 MHz).

---

### Post by fwendt on 2008-02-17
Interesting. While changing jobs, I got a new laptop and tired of the bad battery performance with the old laptop I decided I had enough money to buy a SSD to get more time programming before running out of power. This hasn't really been that much of a great buy yet.
dmesg says it's a 
scsi 2:0:0:0: Direct-Access     ATA      TS32GSSD25S-M    2007 PQ: 0 ANSI: 5
a Transcend 32 GB (slow) 2,5" SATA SSD MLC and as I've had no real time playing with it I just asked gparted to shrink and move partitions/filesystems from the disk that came with the laptop (Thinkpad T61).

Basically, I don't know what filesystem to use to get the best possible performance out of this SSD. If you have any theories I'd be glad to hear them and hopefully test them out.

Thanks in advance, Fredrik

---

### Post by az on 2008-02-17
> **fwendt said:**
> Interesting. While changing jobs, I got a new laptop and tired of the bad battery performance with the old laptop I decided I had enough money to buy a SSD to get more time programming before running out of power. This hasn't really been that much of a great buy yet.
dmesg says it's a 
scsi 2:0:0:0: Direct-Access     ATA      TS32GSSD25S-M    2007 PQ: 0 ANSI: 5
a Transcend 32 GB (slow) 2,5" SATA SSD MLC and as I've had no real time playing with it I just asked gparted to shrink and move partitions/filesystems from the disk that came with the laptop (Thinkpad T61).

Basically, I don't know what filesystem to use to get the best possible performance out of this SSD. If you have any theories I'd be glad to hear them and hopefully test them out.

Thanks in advance, Fredrik

The OLPC XO uses JFFS2.  You can install mtd-tools and create a JFFS2 filesystem using Ubuntu.
[http://packages.ubuntu.com/gutsy/utils/mtd-tools](http://packages.ubuntu.com/gutsy/utils/mtd-tools)

However, I think your device is built to emulate a block device.  I think that jffs2 is meant for hardware that accesses the NAND memory directly.  But I'm not sure.

---

### Post by Sunnz on 2008-02-17
> **gn2 said:**
> If it's for connecting other computers to for internet access, why not just use a router?

It will be cheaper and greener.

Can't find a router that does what I want. There are expensive Cisco one, but they cost way more than my old computer.

---

### Post by BlueKoala on 2008-02-19
Just for the sake of comparing:

Here's the results for a SATA2 750gBs WD HDD

>  sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1652 MB in  2.00 seconds = 825.88 MB/sec
 Timing buffered disk reads:  282 MB in  3.02 seconds =  93.46 MB/sec


Just imagine having 2 of these hot rods in RAID 0  


That would be rocking  :guitar: 

But yeah, I suppose you can't go wrong with a 10$ USB thumb drive =]

---

### Post by Sunnz on 2008-02-21
Ok I tested the boot speed between a SATA2 Raptor at 10'000 RPM and a Flash USB2.0 thumb drive.

The result was... they had exactly the same boot up time!

They were both just running a default installation of OpenBSD, it is very minimal!!

Decisions decisions... should I use the USB as additional SWAP or?

---

### Post by BlueKoala on 2008-02-21
Someone had corrected me earlier on my statement that flash is probably not recommended as swap. It will probably take years for the flash memory to wear out. Although, USB thumbdrives are really cheap and to setup a machine as a router/gateway probably won't take as much disk space as a 10 000rpm drive would offer. I would personally opt for USB and see how it goes. If it explodes one day then I have the comfort of knowing it was a just a USB drive =]

---

### Post by schmolch on 2008-02-28
Fredrik,

you made one big mistake with that SSD you got.
Transcend sells 2 kind of SSDs:

8, 16GB with SLC chips
32GB with MLC (soon SLC as well) chips

The MLC Chips are VERY VERY slow, that's why their 32GB SSD costs ten times less than other SSDs that size.
If you look up the specs at transcend's site the MLC SSD has about 8MB/s write and 3MB/s random write speed.

Return it if you can!


The SLCs on the other side are much better, im using the 8GB SLC SSD and i like it very much. While it has only a modest 28MB/s r/w (8MB/s random write) the ultra-fast access times make a big difference in desktop usage. Alot of delays you usually get are just gone now, like when using the menu, switching between apps, launching apps etc.

---

### Post by mips on 2008-02-28
> **Sunnz said:**
> Can't find a router that does what I want. There are expensive Cisco one, but they cost way more than my old computer.


You could always build your own. OpenBSD would be nice for such a project.

If you want to use flash I would advise Compact Flash via a IDE adapter. This way the compact flash is actually seen as a regular ide drive.

---

### Post by fwendt on 2008-02-28
> **schmolch said:**
> 
The MLC Chips are VERY VERY slow, that's why their 32GB SSD costs ten times less than other SSDs that size. [...] Alot of delays you usually get are just gone now, like when using the menu, switching between apps, launching apps etc.

Yes. I took a chance and I only got 2/4 of what I was hoping for.
+ less power consumption
+ silent operation
- really fast reads -> no big difference from the other drive
- ok writes -> major slow down

It's too late to return the disk and I've almost gotten used to the delays that sometimes occur. Mounting the filesystem (which is ext3) with noatime made the difference between barely usable and acceptable.

8 GB is just too small to really be usable imho.

Thanks anyway. :)

---

### Post by Sunnz on 2008-03-01
> **mips said:**
> You could always build your own. OpenBSD would be nice for such a project.

Yea that's exactly why I started this thread.

> If you want to use flash I would advise Compact Flash via a IDE adapter. This way the compact flash is actually seen as a regular ide drive.

Hmmm didn't know that they existed!

Well I have already pulled on a Flash drive out of a MP3 player that I don't use anymore, plugged in back into the USB port of the back of my computer, and it is up and running now!

---

### Post by mips on 2008-03-01
> **Sunnz said:**
> 
Hmmm didn't know that they existed!


For those that are interested:
[http://www.pcengines.ch/cflash.htm](http://www.pcengines.ch/cflash.htm)
[http://www.addonics.com/products/flash_memory_reader/ad44midecf.asp](http://www.addonics.com/products/flash_memory_reader/ad44midecf.asp)
[http://www.acscontrol.com/Index_ACS.asp?Page=/Pages/Products/CompactFlash/IDE_To_CF_Adapter.htm](http://www.acscontrol.com/Index_ACS.asp?Page=/Pages/Products/CompactFlash/IDE_To_CF_Adapter.htm)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822998002](http://www.newegg.com/Product/Product.aspx?Item=N82E16822998002)

---

