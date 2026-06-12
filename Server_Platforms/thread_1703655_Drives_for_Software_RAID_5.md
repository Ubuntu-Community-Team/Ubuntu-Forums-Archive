---
title: "Drives for Software RAID 5?"
date: 2011-03-09
forum: Server Platforms
---

### Post by kelargo on 2011-03-09
Hi,

I'm looking for advise on which drives to add into my server for software raid 5. I would like to use 2TB drives for the array. 
The server currently boots off a RAID 1 array and I have a couple other drives mounted until I build a RAID 5 array with new drives. I've read horror stories on using Western Digital WD20EARS and Seagate ST32000542AS. So I'm wondering which large drives are best to use in software raid? 

thanks

---

### Post by dtfinch on 2011-03-09
I tend to look at the most popular (say, on Newegg), and see which has the least amount of 1-2 star ratings. [This one](http://www.newegg.com/Product/Product.aspx?Item=N82E16822152245) is looking pretty good if you don't mind 5400rpm instead of 7200.

---

### Post by kelargo on 2011-03-09
thanks. Reliability is more important than speed, to me.. 
I was reading these drive have 4K sectors.. I'm wondering if that has any impact on creating the array?

---

### Post by Vegan on 2011-03-09
Get a RAID card, better performance and 1000x less headache when there is a problem

---

### Post by rubylaser on 2011-03-09
> better performance and 1000x less headache when there is a problem

This is only your opinion.  How do you arrive at this ridiculous statement?  Just a couple quick examples... better performance than what?  My dual core AMD processor with my ( 8 ) 1TB drives can easily saturate a gigabit connection many times over (how fast does a home user need?).   How easily and  quickly do you think he'll be able recover his array if his propriety raid card fails? With mdadm, I can mount these disks in any machine even with a livecd and continue to have access to my data.

Not everyone has hundreds of dollars to throw at a hardware RAID card, and frankly for a home user, I just don't see the point.  It's not like an enterprise application where you're buying on-site support and will have access to get a replacement to you rapidly if it fails.

---

### Post by dtfinch on 2011-03-09
I usually only go for hardware raid if I'm also getting a battery backup for its write cache. That lets you have near-instantaneous random writes with none of the risks.

Without a battery I don't see much difference between software and hardware raids, except that a hardware raid makes booting less raid-aware operating systems off a raid, or booting anything off a non-mirrored raid much easier, and breaking your OS doesn't break your raid.

---

### Post by rubylaser on 2011-03-09
The write cache is a great point, but for home users, I just don't see that being a big selling point.  I would guess that most people are using mdadm to store pictures, videos, music, etc, and primarily reading that data.  Without a write cache, I can still saturate gigabit to writing to my array so I just don't see that being an advantage of hardware vs. software in a home use case.

If I was at work where we have a 10GbE network, I could actually take advantage of the write cache.  I just don't have the money to put something like that in place at home :)

---

### Post by Vegan on 2011-03-09
The problem with a software RAID is when it crashes the OS is down too.

Hardware is not dependent on an OS.

---

### Post by rubylaser on 2011-03-09
Why is the OS down? If you booted from a mdadm RAID1 array and lost a disk it would still boot the same as a hardware array.  If you lost both disks it wouldn't boot.  Are you saying that hardware RAID1 can magically survive this scenario?

If you lose more drives than you have parity, you lose your array whether you're using hardware or software RAID.  If you lose 2 disks in a RAID5 on hardware, your OS is down the same as it would be on software.  I fail to see your point.

---

### Post by jaylark on 2011-03-09
What happens if your RAID card breaks?  Better buy two with identical firmware versions just to be sure!

Hardware RAID definitely has its place, but for normal home use software is usually better.

And to the original question,stay away from the "green" drives.  The aggressive power management on these drives can cause issues.

---

### Post by HankB on 2011-03-09
I've got two RAID setups (Raid 1 - mirroring) that consist of two drives each and I've selected three different manufacturers (including the WDEARS.) Do the horror stories involve sector size? If so, that's a factor with all 2TB drives to the best of my knowledge. They all do that to gain extra capacity. You only need to take a little care to start partitions on sector boundaries evenly divisible by 8 in order to align the partition with true sector boundaries.

I selected low power drives from Seagate, Samsung and WD for my setups. My only real recommendation is to not choose all drives from the same manufacturer and considering buying from different vendors or at different times to avoid getting drives from one manufacturing batch. Every once in a while there's a bad run or a bad design and if you're unlucky to pick a drive that turns out to be a turkey, life can get painful if drives start failing en masse. (FWIW, my Samsung drive has a known firmware bug that causes it to mark blocks as bad if it gets a SMART command while it is writing the block.)

Another concern with drives to use in a RAID is the ability to limit read retries when the firmware encounters a bad block. In a single drive setup, it is best for the drive to take an extended time to try to read the data because inability to do so results in lost data. In a RAID, that is bad behavior since the data can otherwise be recovered. It is better for the drive to quickly report the read failure and allow the RAID controller (H/W or S/W) deal with it rather than time out and conclude the entire drive has failed. (This has not been an issue for me, but for a RAID serving heavier traffic it can be a headache.)

Weighing in on H/W vs. S/W RAID... If you use Linux S/W RAID you can move the RAID drives to any other computer and read data. If you use H/W RAID, you may not be able to access data without the particular RAID H/W used to set it up. That can be an issue if you want to upgrade to a different MoBo or if your H/W RAID controller fails. (I'm not positive this is true, but it is certainly something I'd want to research before I chose a H/W RAID solution.)

Regarding the boot issue for a RAID1 with a failed drive, I suppose if the boot drive is the one that fails, the system will not boot w/out intervention. In that case you would need to access the BIOS function that allows one to select the boot device and boot from the pother drive. Of course you would need to make sure that GRUB is installed on both drives. I'm not sure that is done automatically. My experience with the Ubuntu installers through 10.04 has been less than stellar WRT installing to a RAID.

best,
hank

---

### Post by HankB on 2011-03-09
> **jaylark said:**
> And to the original question,stay away from the "green" drives.  The aggressive power management on these drives can cause issues.
What issues should I be looking for?

thanks,
hank

---

### Post by rubylaser on 2011-03-09
The main thing people see is the drive takes too long to respond and as result, they can get marked faulty and get kicked out of the array.  You can read about this behavior on both finicky hardware raid cards and some software RAID setups.   I personally would avoid the WD Green drives, but Green drives seem to work fine for others even 4K drives as long as you align the sectors. (Seagate, Hitachi, or Samsung). 

If you've setup your mdadm RAID1 properly, and have grub setup to use the fallback disk, you won't have to manually intervene to get your machine to boot in degraded state, it will just work.  
> My experience with the Ubuntu installers through 10.04 has been less than stellar WRT installing to a RAID.
To ensure that this gets setup properly, I always do a standard install, and then setup mdadm RAID1 after the install.

---

### Post by jaylark on 2011-03-09
> **rubylaser said:**
> The main thing people see is the drive takes too long to respond and as result, they can get marked faulty and get kicked out of the array.  You can read about this behavior on both finicky hardware raid cards and some software RAID setups.   I personally would avoid the WD Green drives, but Green drives seem to work fine for others even 4K drives as long as you align the sectors. (Seagate, Hitachi, or Samsung). 


This.  I have one of my computers with WD Green drives and I haven't had problems, but I know of others that have.  I religiously scan my array for errors so if you already have it installed and working, I would just say to stay on top of it so you.can catch catch issues before they become major problems,

---

### Post by JohnnyC35 on 2011-03-09
I have 2 raids, 1 is 4x1.5Tb Green WD, and the other is 3x2Tb Hitatchi Green (or whatever there green drive is). No speed issue here. I didn't hear about having to align the array to 4K clusters before setting it up. They are running fine on 512b clusters (I think that's right... the smallest one)

---

### Post by rubylaser on 2011-03-09
The Hitachi's should be fine as all but their newest drives are not advanced format.  And, depending on what model your 1.5TB WD drives are, those probably aren't advanced format either, so you probably haven't run into a situation where you'd need to align to a 4K drive.

---

### Post by kelargo on 2011-03-09
I have software raid for my boot drives.. Everything, / and /boot. The 750 GB drives are in RAID1.  My chassis allows me to hot swap them.. and I've been able to test the fault tolerance by removing a drive, continues running, reboot, and re-insert the drive. software raid1 works as advertised and I'm happy with it. I have a bunch more SATA ports for more drives and I want to do RAID 5- four drives. I care more about reliability than speed / performance. The data is mostly read from the drives and streamed over the network. The server sits in my basement away from everything. 

So it seems like:
1. avoid green drives, due to power management issues? 
2. adhere to some unique partitioning scheme due to 4K sectors.
3. seems like Hitachi has more thumbs up than either Seagate or WD? 

Know of any good guidelines on dealing with the 4K sectors of these larger drives? 

I thought about getting a hardware raid card, but the issues of not being able to move my drives to another system convinced me software raid is more practicable and reliable in my situation.

---

