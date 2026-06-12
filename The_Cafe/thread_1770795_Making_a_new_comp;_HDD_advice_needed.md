---
title: "Making a new comp; HDD advice needed"
date: 2011-05-29
forum: The Cafe
---

### Post by Jackslaps on 2011-05-29
The computer I'm currently using has a capacity of 1 TB, which is 2/3rds filled. I'm currently going to upgrade to an i5 2500K, which basically requires me to build a new computer, and am looking to buy a 2 TB hard drive. However I don't want to get rid of my 1 TB either and am looking to see if a JBOD config would be recommended. However I hear nothing but bad things about it wherever I go to research, but as far as I know it's the only way to combine the two hard drives together. It's either that or have the 1 TB be external, but I don't like the clutter around my desk, considering I have a small table to work with that can barely fit my mouse and keyboard. 

I'm torn :(

---

### Post by Dustin2128 on 2011-05-29
> **Jackslaps said:**
> The computer I'm currently using has a capacity of 1 TB, which is 2/3rds filled. I'm currently going to upgrade to an i5 2500K, which basically requires me to build a new computer, and am looking to buy a 2 TB hard drive. However I don't want to get rid of my 1 TB either and am looking to see if a JBOD config would be recommended. However I hear nothing but bad things about it wherever I go to research, but as far as I know it's the only way to combine the two hard drives together. It's either that or have the 1 TB be external, but I don't like the clutter around my desk, considering I have a small table to work with that can barely fit my mouse and keyboard. 

I'm torn :(
Not sure about the hard drives, but why not go with a Phenom II if you're buying a new motherboard? i7 is good for ultra high-end stuff, but Phenom IIs have more power for the dollar than an i5. Anyway, after wikipedia made me an expert, a RAID 0 might be what you're looking for- but I don't know how it works with differently sized discs.

---

### Post by Jackslaps on 2011-05-29
> **Dustin2128 said:**
> Not sure about the hard drives, but why not go with a Phenom II if you're buying a new motherboard? i7 is good for ultra high-end stuff, but Phenom IIs have more power for the dollar than an i5. Anyway, after wikipedia made me an expert, a RAID 0 might be what you're looking for- but I don't know how it works with differently sized discs.

I've been thinking about AMD chips as well, maybe I'll switch over to one of their hexacores, but the whole computer build in general is up in the air except for the 2 TB drive. In general it's my first foray into overclocking now that I have the balls for it, and I heard that the 2nd gen i series was great for that, especially where one review said they were able to get their 2600K up to 4.9 Ghz which, in my eyes, is amazin'. 

Also a Raid 0 array limits itself to the smallest drive size for each drive, which is my 1 TB. That means I'll only get to use 1 of the total 2 TB's in the new drive. From what I can tell JBOD doesn't do that, however over half of the information I found on the internet was "DONT USE IT DONT USE IT DONT USE IT DONT USE IT!!!!!!!!!" The Wiki page wasn't entirely useful either.

---

### Post by Dustin2128 on 2011-05-29
> **Jackslaps said:**
> I've been thinking about AMD chips as well, maybe I'll switch over to one of their hexacores, but the whole computer build in general is up in the air except for the 2 TB drive. In general it's my first foray into overclocking now that I have the balls for it, and I heard that the 2nd gen i series was great for that, especially where one review said they were able to get their 2600K up to 4.9 Ghz which, in my eyes, is amazin'. 

Also a Raid 0 array limits itself to the smallest drive size for each drive, which is my 1 TB. That means I'll only get to use 1 of the total 2 TB's in the new drive. From what I can tell JBOD doesn't do that, however over half of the information I found on the internet was "DONT USE IT DONT USE IT DONT USE IT DONT USE IT!!!!!!!!!" The Wiki page wasn't entirely useful either.
I still don't get what you're trying to do, really- I run multiple drives on most of my builds, and they just get detected and are given their own mount points.

On proc: a quick search reveals the cheapest i5s at over 180$. For near the same price, here's a hex core phenom @ 3.7Ghz:[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103913](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103913)

---

### Post by CharlesA on 2011-05-29
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.

A simpler way to do it would be to use the 1TB drive for the OS and use the 2TB drive for the data.

A note about hard drives - I've been running with Hitatchi 2TB 7200RPM drives for a while and haven't had any problems with them (yet).

---

### Post by jiex on 2011-05-31
Hi there - thanks for the discussion on this thread. I hope I might be able to get some advice, as my question is a little like some of the others. I have a PC (on 24/7) that I use as a torrent box also for www browsing and word processing. I have Ubuntu 10.04 and will upgrade to 11.04. Currently I'm running out of space - and will put in a 1TB for system +ordinary files and data and a 2TB for the torrent data. The 2TB does not need speed, but durability, low power, low noise and no irritating sounds like clicking, etc.
My question is: Any recommended HDDs? I have been looking closely at the WD 20EARX  but also a Samsung 2TB (it is 32 MB DRAM).
Maybe I'm approaching this the wrong way. Not sure. Any advice most gratefully received.

---

### Post by CharlesA on 2011-05-31
Go for [one of the Samsung ones]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152245&cm_re=samsung_spinpoint-_-22-152-245-_-Product").

---

### Post by psusi on 2011-05-31
JBOD is bad because if one drive fails, you loose all of the data.  It is better to use the drives separately and manually control what files you put on each drive.  Then if one fails, you only loose those files.  You also can do things like put all of your media on one, and the system on the other, and then when you aren't listening to media, that drive can go to sleep.  Or you could use one as the main drive, and the other for backups.

Remember: if you aren't making regular backups, sooner or later, you WILL loose your data.

---

### Post by CharlesA on 2011-05-31
> **psusi said:**
> 
remember: If you aren't making regular backups, sooner or later, you will loose your data.

+9000!

Also remember to *test* your backups.

---

### Post by jiex on 2011-06-01
> **CharlesA said:**
> Go for [one of the Samsung ones]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152245&cm_re=samsung_spinpoint-_-22-152-245-_-Product").

Thanks CharlesA, most grateful. I have since found out which Samsung it is - the  Samsung F4 204UI. The drive will not/not be used in a raid configuration but only as a storage device, NTFS. Ubuntu will be on another 1 TB drive, config ext4. The system will operate 24/7

Two follow up questions:
(a) I have seen a few people say this drive has problems and specifically a firmware issue if the drive was made prior to Dec 2010. Do you know of any issues in respect of Ubuntu 11.04 - I've googled and no really found any for the configuration I propose.

(b) I wonder how the Samsung is superior to the WD20EARX. I hasten to add, I am tending to the Samsung. 

thanks for your time and trouble replying. I am most appreciative.
Regards
Jim.

---

### Post by CharlesA on 2011-06-01
> **jiex said:**
> Thanks CharlesA, most grateful. I have since found out which Samsung it is - the  Samsung F4 204UI. The drive will not/not be used in a raid configuration but only as a storage device, NTFS. Ubuntu will be on another 1 TB drive, config ext4. The system will operate 24/7

Two follow up questions:
(a) I have seen a few people say this drive has problems and specifically a firmware issue if the drive was made prior to Dec 2010. Do you know of any issues in respect of Ubuntu 11.04 - I've googled and no really found any for the configuration I propose.

(b) I wonder how the Samsung is superior to the WD20EARX. I hasten to add, I am tending to the Samsung. 

thanks for your time and trouble replying. I am most appreciative.
Regards
Jim.

I'm not sure on a.

As for b, I think both are advanced format drives (with 4096 bytes sectors), but the WD drive has double the cache (64MB vs 32MB) but I don't know if that'll have any real effect on performance.

All the 2TB drives I have use 32MB of cache and I haven't noticed any "slowdown" or anything.

---

