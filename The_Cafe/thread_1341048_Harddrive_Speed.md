---
title: "Harddrive Speed?"
date: 2009-11-29
forum: The Cafe
---

### Post by The Real Dave on 2009-11-29
Its that time of year again, and I'm looking at upgrading a few harddrives in my server. The choice is between these two drives

[Samsung Spinpoint EcoGreen F2 500Gb @ 5400rpm]("http://www.memoryc.com/products/description/500GB_Samsung_SpinPoint_EcoGreen_F2_SATA_3_5-Hard_Drive-16MB_cache-5400rpm_/index.html")

and 

[Samsung Spinpoint F1 500Gb @ 7200rpm]("http://www.memoryc.com/storage/internalharddrive/500gbsamsungf1spinpointsata2.html")

Will the RpM make a big difference? These drives are going to be in a server, not accessed too often, and nothings booting from them. Also, they're gonna be connected through a SATA RAID card, I'm probably not going to upgrade that. Does the extra speed of the 7k2 drive out weight the environmental, heat and energy benefits of the EcoGreen? The EcoGreen is also marginally cheaper... 

Opinions would be great :)

---

### Post by insane_alien on 2009-11-29
if its in a server(especially one that isn't accessed to often) then the 5400rpm one will do. its not going to be slow and the biggest cause of slow down is likely to be the network anyways. increasing the hardrive speed would have minimal improvements.

a use case for a faster drive is if the server is performing very disk intensive applications and not requiring too much network.

basically just ask yourself, is the task it needs to perform disk intensive? 

if yes then 7200RPM(or a nice 10k or 15k if your willing to spend and need it)

if no then 5400RPM cause its a bit cheaper.

---

### Post by cascade9 on 2009-11-29
For a server, get the Eco Green. In modern drives, the 7200 models tend push less than %15 faster than the 5400 'green power/eco green' etc drives. I'd expect over 75MB/sec from the eco green (probably more like 100MB/sec) Tons of speed. 

I'm running a WD 1TB Green Power drive for desktop use, mainly for the energy/heat issues...but I must admit that the price difference was the final push (I paid $115 AU for the GP drive, the 7200 1TB was over $170).

---

### Post by Exodist on 2009-11-29
> **The Real Dave said:**
> Its that time of year again, and I'm looking at upgrading a few harddrives in my server. The choice is between these two drives

[Samsung Spinpoint EcoGreen F2 500Gb @ 5400rpm]("http://www.memoryc.com/products/description/500GB_Samsung_SpinPoint_EcoGreen_F2_SATA_3_5-Hard_Drive-16MB_cache-5400rpm_/index.html")

and 

[Samsung Spinpoint F1 500Gb @ 7200rpm]("http://www.memoryc.com/storage/internalharddrive/500gbsamsungf1spinpointsata2.html")

Will the RpM make a big difference? These drives are going to be in a server, not accessed too often, and nothings booting from them. Also, they're gonna be connected through a SATA RAID card, I'm probably not going to upgrade that. Does the extra speed of the 7k2 drive out weight the environmental, heat and energy benefits of the EcoGreen? The EcoGreen is also marginally cheaper... 

Opinions would be great :)


This is only a question you can answer.
- What are the task this server will perform?
- Whats the average user workload?
- How fast do you need this system to be?

IMHO:
- 5400RPM for long life file servers that dont get accessed by many users or put in a heavy workload for long periods.
- 7200RPM for SOHO multi-task servers, I.e. Home/SmallBusiness Website & File Hosting with medium to heavy workloads.
- 10,000RPM for large business with constant heavy web traffice and constant heavy file transfer demands.

Its not always the over all data transfer rate as drive Seek times are VERY important.

In addition if you going with a performance raid setup, dont gimp yourself by getting a slower drive. But if RAID mirroring for data integrity is you purpose, then a 5400 could be a good option depending on the above facts.

---

### Post by The Real Dave on 2009-11-29
> **Exodist said:**
> This is only a question you can answer.
- What are the task this server will perform?
- Whats the average user workload?
- How fast do you need this system to be?

IMHO:
- 5400RPM for long life file servers that dont get accessed by many users or put in a heavy workload for long periods.
- 7200RPM for SOHO multi-task servers, I.e. Home/SmallBusiness Website & File Hosting with medium to heavy workloads.
- 10,000RPM for large business with constant heavy web traffice and constant heavy file transfer demands.

Its not always the over all data transfer rate as drive Seek times are VERY important.

In addition if you going with a performance raid setup, dont gimp yourself by getting a slower drive. But if RAID mirroring for data integrity is you purpose, then a 5400 could be a good option depending on the above facts.


It won't be doing much work at all, a home server for 4 computers. The heaviest load it's gonna have is probably gonna be streaming media. It isn't accessed a whole load. It's gonna be in RAID0, so not looking for data integrity.

I think I'll go with the EcoGreen. The lower power consumption will be nice, seeing as the server is 24/7 and having less heat output is good two. I just wanted to know how big of a difference there is between 7k2 and 5k4 rpm drives :) 

Thanks to all who posted :)

---

### Post by Exodist on 2009-11-29
> **The Real Dave said:**
> It won't be doing much work at all, a home server for 4 computers. The heaviest load it's gonna have is probably gonna be streaming media. It isn't accessed a whole load. It's gonna be in RAID0, so not looking for data integrity.

I think I'll go with the EcoGreen. The lower power consumption will be nice, seeing as the server is 24/7 and having less heat output is good two. I just wanted to know how big of a difference there is between 7k2 and 5k4 rpm drives :) 

Thanks to all who posted :)

Really tho, 5400RPM is a good choice for what you want. But unless your just stripping your drives for the sake of having one large drive. The benefit of going RAID0 will mostly be lost. Just save your self the trouble and dont setup the RAID. IMHO..
RAID0 isnt true RAID anyway, its just stripping both(or more) drives to gain more speed by throw equal amounts of data across the drives. The slower access and read/write speeds on the drive(s) will offset the raid advantage. IMHO

---

### Post by gn2 on 2009-11-29
Expensive for just 500gb, both models are supreceded by [the newer and faster F3]("http://www.ebuyer.com/product/173804").

Also the [1.5tb EcoGreen F2]("http://www.ebuyer.com/product/166989") works out cheaper per gb.

[http://www.tomshardware.com/charts/2009-3.5-desktop-hard-drive-charts/benchmarks,50.html](http://www.tomshardware.com/charts/2009-3.5-desktop-hard-drive-charts/benchmarks,50.html)

---

### Post by The Real Dave on 2009-11-29
> **gn2 said:**
> Expensive for just 500gb, both models are supreceded by [the newer and faster F3]("http://www.ebuyer.com/product/173804").

Also the [1.5tb EcoGreen F2]("http://www.ebuyer.com/product/166989") works out cheaper per gb.

[http://www.tomshardware.com/charts/2009-3.5-desktop-hard-drive-charts/benchmarks,50.html](http://www.tomshardware.com/charts/2009-3.5-desktop-hard-drive-charts/benchmarks,50.html)

A Tb for €30 more....its tempting....but that would really be overkill I think...there's no way I could fill a Tb. But damn its tempting....

---

### Post by Exodist on 2009-11-29
> **The Real Dave said:**
> A Tb for €30 more....its tempting....but that would really be overkill I think...there's no way I could fill a Tb. But damn its tempting....
Its better to go with a oversized drive. The reason is the drive will put data toward the center of the drive first, the data that ends up on the out sections of the plater(s) will accessed slower. So a 1TB drive using only 500MB will keep more your data toward the center of the platters keeping the speed up.

---

### Post by The Real Dave on 2009-11-29
> **Exodist said:**
> Its better to go with a oversized drive. The reason is the drive will put data toward the center of the drive first, the data that ends up on the out sections of the plater(s) will accessed slower. So a 1TB drive using only 500MB will keep more your data toward the center of the platters keeping the speed up.

Hmmm, I suppose its future proofing at least :)

---

### Post by toupeiro on 2009-11-29
If you're looking at the difference in price between a 10K and a15K and you're still looking at SATA you're doing it wrong.  You can get a SAS 10K drive which will blow the doors off a SATA 10K drive for not very much more at all due to SCSI's read/write architecture.  15K SATA is silly to me.  Even if you got a 7.2K SAS disk its still going to win out a SATA disk.  Many motherboards support SAS on board now, and SAS controllers are not too expensive..  I say sata wins if you need lots of drive space and you dont care how fast it is (e.g.media archival)  If you want speed on a sata controller, and you're looking at 15K sata disks, I'd just go SSD.  SSD has a write penalty so if you do a lot of writing to disk, nothing will outperform a SAS disk within an affordable range.

OP: I'd go with the 7200 disk if anything will be initiated from that disk (e.g: OS and applications), but if you're just throwing a bunch of videos and mp3's on there, the 5400 will do you just fine.  I would seriously consider SAS for speed+size and SSD for raw load speed if this disk is going to be an OS disk or if any applications will be installed directly to it because it makes a world of a difference.

---

### Post by markp1989 on 2009-11-29
> **gn2 said:**
> Expensive for just 500gb, both models are supreceded by [the newer and faster F3]("http://www.ebuyer.com/product/173804").

Also the [1.5tb EcoGreen F2]("http://www.ebuyer.com/product/166989") works out cheaper per gb.

[http://www.tomshardware.com/charts/2009-3.5-desktop-hard-drive-charts/benchmarks,50.html](http://www.tomshardware.com/charts/2009-3.5-desktop-hard-drive-charts/benchmarks,50.html)

the 1.5tb eco green drives are nice, i have 2 in my server/htpc , nice and quiet :D  

i just use them for storage, i chose the 5400rpm drives for noise reasons,

---

### Post by gn2 on 2009-11-29
For use inside a typical PC case the rpm doesn't affect noise very much if you mechanically de-couple the drive from the chassis, either by using a no-vibes cage, a lump of foam in the base or suspend the drive on bungees.

---

### Post by The Real Dave on 2009-11-30
Thanks for the replies guys, though, I'm still not sure whether to get the EcoGreen or a Tb

---

### Post by gn2 on 2009-11-30
Just buy what you can afford, as they're all Samsungs you will be buying an excellent drive whichever one you get.
If it was me shopping for file storage, I would go for size over speed.
For running an OS and applications, speed over size.

---

### Post by The Real Dave on 2009-11-30
> **gn2 said:**
> Just buy what you can afford, as they're all Samsungs you will be buying an excellent drive whichever one you get.
If it was me shopping for file storage, I would go for size over speed.
For running an OS and applications, speed over size.

Cool :) Thanks for the advice :)

---

### Post by cascade9 on 2009-12-01
> **Exodist said:**
> 
 IMHO:
 - 5400RPM for long life file servers that dont get accessed by many users or put in a heavy workload for long periods.
 - 7200RPM for SOHO multi-task servers, I.e. Home/SmallBusiness Website & File Hosting with medium to heavy workloads.
 - 10,000RPM for large business with constant heavy web traffice and constant heavy file transfer demands. 

I pretty much agree, apart from the way that the newer 5400s are really closing the gap between 5400s and 7200s. Also, I'd say 10,000RPM SAS/SCSI drives only, I wouldnt put a 10K Raptor/Velociraptor into a business server. 
 
 > **Exodist said:**
> Its not always the over all data transfer rate as drive Seek times are VERY important. 
 
True, but its not that huge a difference. Eg. My 1TB WD Green Power (32MB model) does 7.23/14.03 (write/read). The full WD 7200 Caviar Black is 5.68/12.29 and the WD RE3 5.33/12.15. Which isnt that much of a differnce. Some of the 7200 RPM drives are very similar or  _worse_ than the 5400-

[http://www.xbitlabs.com/articles/storage/display/1tb-14hdd-roundup_10.html](http://www.xbitlabs.com/articles/storage/display/1tb-14hdd-roundup_10.html)

BTW, thats just one page from a very good test, well worth a read if you've got much intrest in hard drives. 

> **Exodist said:**
> Really tho, 5400RPM is a good choice for what you want. But unless your just stripping your drives for the sake of having one large drive. The benefit of going RAID0 will mostly be lost. Just save your self the trouble and dont setup the RAID. IMHO..
RAID0 isnt true RAID anyway, its just stripping both(or more) drives to gain more speed by throw equal amounts of data across the drives. The slower access and read/write speeds on the drive(s) will offset the raid advantage. IMHO

Agreed. RAID0 isnt worth the trouble IMO, it would be better to have a decent backup strategy. Or spend a tiny bit more and get a 3rd drive for RAID5. 

@ The Real Dave- I'm also very wary of running different brand/model Hdds in a RAID arrary. If your getting just 1 drive to make this RAID1 arrary with a 2nd drive you already have, I really wouldnt fo that. 

> **toupeiro said:**
> If you're looking at the difference in price between a 10K and a15K and you're still looking at SATA you're doing it wrong.  You can get a SAS 10K drive which will blow the doors off a SATA 10K drive for not very much more at all due to SCSI's read/write architecture.  15K SATA is silly to me.  Even if you got a 7.2K SAS disk its still going to win out a SATA disk.  Many motherboards support SAS on board now, and SAS controllers are not too expensive..  I say sata wins if you need lots of drive space and you dont care how fast it is (e.g.media archival)  If you want speed on a sata controller, and you're looking at 15K sata disks, I'd just go SSD.  SSD has a write penalty so if you do a lot of writing to disk, nothing will outperform a SAS disk within an affordable range.

There are no 15K SATA drives. As far as I know anyway. 

SAS (and SCSI) is great, but it very pricey. Even the 7200s are a lot more than SATA here, and the 15K drives are mega expensive. I'm sure I could get 3x WD GP 1TB drives for about the cost of a single 146GB 15K SAS drive. While I'm also sure that the SAS drives will have a higher MTBF, I doubt that a single SAS will outrun or outlast 3 x SATA in RAID5. The lifespan is very debatable though. 

15K drives have great access times, but you really pay for that when you go to buy them, also in heat. 

> **toupeiro said:**
> OP: I'd go with the 7200 disk if anything will be initiated from that disk (e.g: OS and applications), but if you're just throwing a bunch of videos and mp3's on there, the 5400 will do you just fine.  I would seriously consider SAS for speed+size and SSD for raw load speed if this disk is going to be an OS disk or if any applications will be installed directly to it because it makes a world of a difference.

5400s can be fine even for OS/desktop use. When I changed from a SATA Seagate 7200 (7200.8 or 7200.9 I think, got rid of the drive so I cant check) and put in my 5400, it was quite a bit faster. If your going for as much speed as you can get, in a single drive, yeah, agreed, go for the 7200 or a SSD. But the modern 5400s will blow the doors of older 7200s, and arent even that much slower than a 7200 of similar age.

---

### Post by The Real Dave on 2009-12-01
> **cascade9 said:**
> 
Agreed. RAID0 isnt worth the trouble IMO, it would be better to have a decent backup strategy. Or spend a tiny bit more and get a 3rd drive for RAID5. 

@ The Real Dave- I'm also very wary of running different brand/model Hdds in a RAID arrary. If your getting just 1 drive to make this RAID1 arrary with a 2nd drive you already have, I really wouldnt fo that. 

The RAID0 isn't really for performance, I've yet to been able to set up a performance RAID0, the controller has usually been the bottleneck. 

The RAID0 was really only to get it to act as one large disk. I'm not looking for redundency. Is it bad to RAID0 drives of varying sizes?

---

### Post by cascade9 on 2009-12-01
Opps, I mistyped before RAID1 instead of RAID0. Sorry ;) 

As you just want to make one big disc...why hot just get a bigger Hdd?

I really wouldnt mix and match different size Hdds. I've heard of nasty issues when people did that. Anyway, even if you do that, RAID size will be that of the smallest disc. Considering that hdds have picked up speed, it may, and probably will, end up slower than a single disc (esp. once you count RAID overheads) 

BTW, if you lose one disc on a RAID0 array, you lose the whole array. Data, gone. Maybe JBOD (just bunch one disc) might be a a better choice if you really want a single partition over several drives.

---

