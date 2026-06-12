---
title: "Questions about HD's, sata 3 vs 6gb/s, and general performance"
date: 2010-09-11
forum: The Cafe
---

### Post by NMFTM on 2010-09-11
This is would normally be the kind of thing I'd do my own research on. But I sort of have a lot of balls up in the air right now and would like to order a new HD ordered by at least Monday morning.

I currently have two [Samsung Spinpoint F3 1TB]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152185&cm_re=samsung_spinpoint_1tb-_-22-152-185-_-Product") drives fake raid0'd together for all of my needs. From data storage to my multiple booted OS's.

I took a 750GB Western Digital drive out of my external enclosure but upon performing tests, it can apparently only read at about 65MB/s while my 2TB raid0 can read at about 140MB/s, according to Ubuntu's Disk Manager benchmarks.

I planned on using the 750 as my primary and dedicating the raid0 array for data usage only. But, I don't want to downgrade to something that's read time is almost 50% slower. So, I'm looking for a new 750GB drive to use as my primary.

I don't know if the read rates on my Spinpoint F3 fake raid0 array is because they're raid'd together or because they're just faster drives in general. Because I've never done test on them independently and currently don't have the time to repartition and test it out. I've had people tell me that fake raid0 with a JMicron controller (they're supposedly kinda crappy) will give me everything from worse, to neutral, to superior performance than if they were not fake raid'd.

I was looking at getting a WD Caviar Black because for being their high performance drives many of them aren't terribly expensive. But, I don't currently have the time to research if other companies that aren't as name brand of them sell drives with similar performance for a much lower price.

Also, what about the new SATA 6gb/s drives? Would it be worth it to get one? They're not that much more expensive than 3gb/s ones. But, what I'm concerned about is that I'd need to get a SATA 6gb/s PCI-E card. After checking Newegg [most of them]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=40000410&IsNodeId=1&Description=sata%206gb%2Fs&bop=And&Order=PRICE&PageSize=20") are over $100. But there are some that are in the $20-50 range. Are these cheaper ones just as good as the more expensive ones or do the cheaper ones not give you the full speed that sata 6gb/s is capable of? Also, is it even worth it to upgrade to 6gb/s if I'm not going to be using a solid state drive?

If I do this I'll probably end up putting my OS's on the new 750GB drive, my virtual machines on the slower 750GB drive, and my data on the 1TB fake raid0 array. That way I'll be able to do a lot of multitasking without all the burden being put on a single drive.

Unfortunately researching HD's isn't easy because they don't give you speed in terms of transfer rates or access times. Only seek time and latency, which Disk Manager's benchmark tool doesn't show you. Plus, most people only look at the RPM and storage ratings and buy the cheapest drive available because they falsely assume that all 7200RPM drives perform the same and it's only the storage capacity that matters. Which seems to be how most companies market their drives.

---

### Post by NMFTM on 2010-09-12
> **NMFTM said:**
> After checking Newegg [most of them]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=40000410&IsNodeId=1&Description=sata%206gb%2Fs&bop=And&Order=PRICE&PageSize=20") are over $100. But there are some that are in the $20-50 range. Are these cheaper ones just as good as the more expensive ones or do the cheaper ones not give you the full speed that sata 6gb/s is capable of?
What I meant was: I checked the stats on the $20 vs $100 range devices and both say they get up to 6gb/s. But, that's just a theoretical possibility that I'm not naive enough to think they actually transfer at consistently and outside of a laboratory. If both devices get "up to" X speed, would a more expensive controller get up to that speed more often than a cheaper device with a cheaper sata 6gb/s controller in it?

---

### Post by blueturtl on 2010-09-12
You have to understand that the interface speed that is given (UDMA100, SATA 3 GB/s, SATA 6 GB/s) is just that, the maximum speed the interface can transmit. The harsh truth is that in hard drives the bottle necks lie in the mechanics rather than the interface: you can't find a drive that can actually reach the maximum speed of the interface. SATA 6 GB/s is futureproof I guess, but at this point mostly just marketing. Two drives differing *only* in the interface will have equal performance.

Your RAID0 is the reason for the speed difference you've reported, because the data on RAID0 is read half from one disk, half from the other simultaneously. I doubt there is a big performance difference if the drives were matched against each other individually.

edit: Anyway, there are some sites like StorageReview.com which have drive model performance statistics to read, you should check that site if you want to get some general idea of how different brand/model HDDs actually perform.

---

### Post by Lensman on 2010-09-12
Some interesting questions. Assuming you don't want to go the SSD route, I might be inclined to use your RAID array as your primary OS drive and set an automatic backup to a 2T Spinpoint. As for the new 6Gbs drives, I am not so sure that most are not even saturating their 3Gbs drives. As for the WD Black drives, they are an excellent choice.

---

### Post by cascade9 on 2010-09-12
+1 to blueturtl. 

If you are goign to a single drive primary (I'm assuming that you would be running your OS/es from that drive), RAID0 would be pointless. Sure, it would read and write faster than a signle drive, but the extra 'speed' would be poinltess....as your reading, and writing will be limited to the speed of the single drive. Anyway....

A single Spinpoint would be fairly similar in speed to the 750Gb WD drive, like blueturtl said. (I'd guess that it would be a caviar blue, or a green power drive). 

@Lensman- SATAI hasnt even been saturated yet. I havent seen any single drive break 150MB/sec yet. 

SATAIII is pretty much just marketing for mechanical HDDs. Some of the SSDs have satutared SATAII though, so thats only true from mechanical HDDs. 

If you did move to SATAIII drives, they should run fine on a SATAII, and probably even a SATAI controller. If it didnt (slim chance) then I know that the WD SATAIII drives have a jumper to limit the interface to SATAII...I dont know if Seagate, Samsung, Hitachi drive have a limiting jumper. 

BTW, if you wanted to see a good comparison between theb different drive manufacturers and models, this is decent test (if a lillte out of date)-

[http://www.xbitlabs.com/articles/storage/display/1tb-14hdd-roundup.html](http://www.xbitlabs.com/articles/storage/display/1tb-14hdd-roundup.html)

Slightly newer version- 

[http://www.xbitlabs.com/articles/storage/display/1tb-hdd-roundup-3.html](http://www.xbitlabs.com/articles/storage/display/1tb-hdd-roundup-3.html)

---

### Post by NMFTM on 2010-09-12
> **blueturtl said:**
> You have to understand that the interface speed that is given (UDMA100, SATA 3 GB/s, SATA 6 GB/s) is just that, the maximum speed the interface can transmit. The harsh truth is that in hard drives the bottle necks lie in the mechanics rather than the interface: you can't find a drive that can actually reach the maximum speed of the interface. SATA 6 GB/s is futureproof I guess, but at this point mostly just marketing.
Well, I thought that the SataIII HD's might have had multiple read/write heads per disk like some of the server drives I've heard about which would actually make use of the new interface. Although, thinking about it now and after doing the numbers I realize that they'd cost a lot more than they do if that were the case. Those drives are probably only for SCSI.
> **Lensman said:**
> I might be inclined to use your RAID array as   your primary OS drive and set an automatic backup to a 2T   Spinpoint.
My theory behind using the 2TB RAID0 array for storage and a   single 750GB drive for OS's was to get away from using RAID for my   OS's because I think that might be the reason Windows 7 BSOD's all the   time. I do have a Hitachi (Cavalry) 2TB drive. But I use that for  backing up my data. I keep it unplugged and in a metal cabinet so that  if my house got hit by lightning it wouldn't be inside my computer and  so that if its' not powered on all the time it's less likely to  spontaneously crash, as unlikely as those two scenarios are.

I think I might go the route of just getting a 2TB storage drive, use my  2TB fake0 array for primary OS's, and not worry about Windows 7's  instability. Or hope that it's fixed in the form of either a Windows or  BIOS update.

---

