---
title: "SD cards the next harddrives?"
date: 2009-02-21
forum: The Cafe
---

### Post by SonnHalter on 2009-02-21
My dad was talking about how he heard that some people were making sd cards as big as harddrives, and hold 120gb. It saves a lot of time because the files are instant. A regular harddrive has to spin but a sd card doesn't. 

anyone else hear of this/

---

### Post by damis648 on 2009-02-21
He is a bit misinformed. He is thinking of SSD's (Solid-State Drives) which use flash memory like RAM and Flash Drives which makes them much faster than traditional Hard Drives which spin, as well as more power efficient.
See [http://en.wikipedia.org/wiki/Solid-state_drive](http://en.wikipedia.org/wiki/Solid-state_drive)
and [http://www.google.com/products?q=SSD&oe=UTF-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&ie=UTF-8&sa=N&tab=wf&ei=W4-gSbfGG8XT-QafhYi2Dg&oi=property_suggestions&resnum=0&ct=property-revision&cd=3](http://www.google.com/products?q=SSD&oe=UTF-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&ie=UTF-8&sa=N&tab=wf&ei=W4-gSbfGG8XT-QafhYi2Dg&oi=property_suggestions&resnum=0&ct=property-revision&cd=3)

---

### Post by Muffinabus on 2009-02-21
There are a few disadvantages with SSD's right now though.  Limited write cycles, slower write speeds (I think?), and much smaller capacity with more expensive prices.

---

### Post by damis648 on 2009-02-21
> **Muffinabus said:**
> There are a few disadvantages with SSD's right now though.  Limited write cycles, slower write speeds (I think?), and much smaller capacity with more expensive prices.

On the contrary, all of those are in fact the improvements of SSD's over HDD's. They have much greater speeds over HDD's (over 2x or 3x the speed for the ones I've seen, thats 100mb/s vs 200mb/s and even 300mb/s). Yes, they are more expensive, but well worth it if you need the speed and reliability.

---

### Post by Skripka on 2009-02-21
> **damis648 said:**
> On the contrary, all of those are in fact the improvements of SSD's over HDD's. They have much greater speeds over HDD's (over 2x or 3x the speed for the ones I've seen, thats 100mb/s vs 200mb/s and even 300mb/s). Yes, they are more expensive, but well worth it if you need the speed and reliability.

On Read cycle I'd agree with you...Write cycles tend to be slower than a good or highspeed HDD.  Also SSDs are fussy with regards to formmating and file system.

A 10 or 15k RPM HDD I'd take anyday for scratch disk space.  For a boot volume that doesn't see much writing, I'd use an SSD.

---

### Post by Rumbl3 on 2009-02-21
Yeah i almost bought two patriot 32gig ssd's yesterday on newegg. But i found a article on my forum i hang out on. was pretty interesting.

[http://www.ocforums.com/showthread.php?t=596362](http://www.ocforums.com/showthread.php?t=596362)

So i decided to just be cheap anyway lol so my gf don't have a fit and i bought two 250 gig WD drives to raid 0 with. My drives right now are old IDE drives i got for free. So moving to sata with 16mb cache instead of 2 will be nice lol.

But i will say benchmarks from the SSD drives are insane for read times. I know you have to do some tweaking so stuff like firefox isn't writing to it all the time etc.

They will be the future most likely but they still have some work to do with them. For right now i would say go with Vraps (velociraptors from wd) if you want hardcore speed and storage.

---

### Post by smartboyathome on 2009-02-21
By the way, most of the ones with slow write speeds are MLC ones. SLC are much faster, and in fact I've seen them have just as good write times as read times.

---

### Post by tom66 on 2009-02-21
Write speed on SSDs is just about now on-par with HDDs, or at least that's what I've been told. 

Also, the write cycle limit is not really a problem due to the: a) fact that it is often 1+ million for most new SSDs; and b) they perform wear-leveling to reduce problems.

The only problem I see at the moment is that they are much more expensive than traditional HDDs.

SD cards are different, they are cheaper, slower and only do around 100k writes.

---

### Post by forcecore on 2009-02-21
has anyone tested ubuntu on ssd, is it faster like bootup, file managment, copyng etc...?

---

### Post by miggys on 2009-02-21
Just to bring this back to what the original poster was talking about:

[http://www.sdcard.org/developers/tech/sdxc](http://www.sdcard.org/developers/tech/sdxc)

---

### Post by Skripka on 2009-02-21
> **miggys said:**
> Just to bring this back to what the original poster was talking about:

[http://www.sdcard.org/developers/tech/sdxc](http://www.sdcard.org/developers/tech/sdxc)

Unfortunately you need a bus with a great deal more cajones than USB2 to make that worth your while....Oh, well USB will come some time next year thereabouts.

---

### Post by fistfullofroses on 2009-02-21
Can you give me a reference for 1,000,000+?
I am not doubting it, I just want to know which manufacturer(s) is/are offering a drive like that.

I think that solid state is the way to go. Write life is shorter, but there is no chance of mechanical failure, so the longevity of the drive is really about equal. Solid state also uses less power, and seek time is non-existant. Solid state drives are also more durable (once again due to the lack of moving parts). So, if Tom66 is correct.... even for the price upfront... it may be worth it.

---

### Post by Polygon on 2009-02-21
don't ssd's wear out a lot faster? almost like a usb flash drives where it only has so many write cycles before it just cant hold info any more?

---

### Post by tom66 on 2009-02-22
Source: [http://www.storagesearch.com/ssdmyths-endurance.html](http://www.storagesearch.com/ssdmyths-endurance.html)

and, from Wikipedia:

> Limited write (erase) cycles: Flash-memory cells will often wear out after 1,000 to 10,000 write cycles for MLC, and up to 100,000 write cycles for SLC[11], while high endurance cells may have an endurance of 1–5 million write cycles (many log files, file allocation tables, and other commonly used parts of the file system exceed this over the lifetime of a computer).[26] Special file systems or firmware designs can mitigate this problem by spreading writes over the entire device (so-called wear levelling), rather than rewriting files in place.[27] In 2008 wear levelling was just beginning to be incorporated into consumer level devices.[11] However, effective write cycles can be much less, because when a write request is made to a particular memory block, all data in the block is overwritten even when only part of the memory is altered. The write amplification, as referred by Intel, can be reduced using write memory buffer.[28] In combination with wear leveling, over-provisioning SSD flash drives with spared memory capacity also delays the loss of user-accessible memory capacity. NAND memory can be negatively impacted by read and program (write) disturbs arising from over accessing a particular NAND location. This overuse of NAND locations causes bits within the NAND block to erroneously change values. Wear leveling, by redirecting SSD writes to lesser-used NAND locations, thus reduces the potential for program or write disturbs.[29] An example for the lifetime of SSD is explained in detail in this wiki.[dubious – discuss] SSDs based on DRAM, however, do not suffer from this problem.

[http://en.wikipedia.org/wiki/Solid-state_drive](http://en.wikipedia.org/wiki/Solid-state_drive)

---

### Post by billgoldberg on 2009-02-22
> **SonnHalter said:**
> My dad was talking about how he heard that some people were making sd cards as big as harddrives, and hold 120gb. It saves a lot of time because the files are instant. A regular harddrive has to spin but a sd card doesn't. 

anyone else hear of this/

Solid State Drives are the next Hard Drives.

Sure sd cars will get bigger, but they won't be replacing your hdd or ssd.

---

### Post by billgoldberg on 2009-02-22
> **Polygon said:**
> don't ssd's wear out a lot faster? almost like a usb flash drives where it only has so many write cycles before it just cant hold info any more?

You should get at least 5 years out of an modern SSD drive.

That's pretty good.

Also when the write cycles wear out, the drive goes into read only mode. So you'll never loose the data on it.

---

### Post by jnw222 on 2009-02-22
i have, it just works as a regular hdd with some changes

1. lower power usage
2. faster preformance
3  fragmentation doesn't slow the hard drive on windows as much
4. no noise

---

### Post by infoseeker on 2009-02-22
If I were a harddrive manufacturer and my company wasn't doing development in  SSD technology then I think I would be concerned about the future of the company ;)

Anyone remember the floppy drive or stiffy drive?

---

