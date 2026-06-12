---
title: "Need your help - Find me a laptop!"
date: 2011-10-10
forum: The Cafe
---

### Post by ELD on 2011-10-10
Ok Ubuntu folk i am looking for a laptop at a max of £600.

It needs to have a semi-decent graphics chip and _NOT_ have nvidia optimus (since linux doesn't support it) - finding one without optimus is proving very difficult!

Needs to deliver to the UK.

---

### Post by collisionystm on 2011-10-10
[http://configure.us.dell.com/dellstore/config.aspx?oc=bqctt2&c=us&l=en&s=bsd&cs=04&model_id=vostro-v131](http://configure.us.dell.com/dellstore/config.aspx?oc=bqctt2&c=us&l=en&s=bsd&cs=04&model_id=vostro-v131)

Processor	2nd generation Intel®Core&#8482; processor i3-2330M (2.20GHz) with Intel HD Graphic 3000
Operating System	Ubuntu version 11.04
Display	13.3 inch High Definition LED Display (1366 x 768) with anti-glare
Memory2	2GB2 Single Channel DDR3 SDRAM at 1333MHz
Hard Drive	320GB3 SATA hard drive (7200RPM)
Optical Drive
Warranty	1 Year Basic Limited Warranty and 1 Year NBD On-Site Service
Advertised System Weight	3.6 lbs

---

### Post by ubupirate on 2011-10-10
> **collisionystm said:**
> Intel HD Graphic 3000

OP asked for semi-decent graphics chip.

---

### Post by ELD on 2011-10-10
(needs to be available in UK hence the £ mate)

> **ubupirate said:**
> OP asked for decent graphics chip.

Also yes no intel graphics.

---

### Post by collisionystm on 2011-10-10
> **ubupirate said:**
> OP asked for semi-decent graphics chip.

That is a semi decent graphics chip.

Obviously you have never had that series.

Radeon sucks. He does not want nvidia. So whats left?

---

### Post by ELD on 2011-10-10
> **collisionystm said:**
> That is a semi decent graphics chip.

Obviously you have never had that series.

Radeon sucks. He does not want nvidia. So whats left?

Actually i stated no nvidia optimus - it's a certain type, nvidia on its own is perfectly fine.

---

### Post by ubupirate on 2011-10-10
> **collisionystm said:**
> That is a semi decent graphics chip.

Obviously you have never had that series.

Radeon sucks. He does not want nvidia. So whats left?

I've been an Intel graphics chip user for the longest time now, and recently in the past 6 months switched over to AMD/ATI and I would NEVER go back to Intel again. Intel has problems on Windows alone, nevermind on Linux.

Supported nVidia or AMD/ATI would be OP best bet, especially a good AMD/ATI card as AMD provides more bang for the buck over nVidia with slightly less mature drivers (but they are growing more mature with each release).

---

### Post by ELD on 2011-10-10
Yes i currently have AMD/ATI in my desktop and run without a problem i would consider both. But no intel.

---

### Post by 3Miro on 2011-10-10
Here is some information about the current state of Linux graphics on laptops:

[http://ubuntuforums.org/showthread.php?t=1845816](http://ubuntuforums.org/showthread.php?t=1845816)

In short:

Nvidia only works with high end GPUs of 560+ or 460+. Those are very expensive, powerful and eat your battery in minutes. Low end Nvidia is all Optimus and doesn't work on Linux.

ATI/AMD laptops are rare (at least in USA). ATI graphics usually comes with AMD CPU and their latest products seem to be somewhat unpopular on laptops (I don't know if it is for a good or for a bad reason). With ATI you also need proprietary drivers to get good battery life. You should use at least Radeon 4xxx or newer.

Cheaper Radeon graphics is about on the same level as the current Intel HD 3000. Overall for Laptops, Intel is the probably the best choice in terms of performance, price, compatibility and availability. I have a System76 Pangolin and I have no issues with Unity effects or Video.

---

### Post by drawkcab on 2011-10-10
> **3Miro said:**
> Here is some information about the current state of Linux graphics on laptops:

[http://ubuntuforums.org/showthread.php?t=1845816](http://ubuntuforums.org/showthread.php?t=1845816)

In short:

Nvidia only works with high end GPUs of 560+ or 460+. Those are very expensive, powerful and eat your battery in minutes. Low end Nvidia is all Optimus and doesn't work on Linux.

ATI/AMD laptops are rare (at least in USA). ATI graphics usually comes with AMD CPU and their latest products seem to be somewhat unpopular on laptops (I don't know if it is for a good or for a bad reason). With ATI you also need proprietary drivers to get good battery life. You should use at least Radeon 4xxx or newer.

Cheaper Radeon graphics is about on the same level as the current Intel HD 3000. Overall for Laptops, Intel is the probably the best choice in terms of performance, price, compatibility and availability. I have a System76 Pangolin and I have no issues with Unity effects or Video.

I agree.

Nvidia sans optimus can be had but beyond your price range unless you want to go lower end so that there really isn't much of an advantage over the intel 3000.

I bet you could find a really nice Lenovo thinkpad with AMD/ATI (the newer stuff runs just fine) or Intel 3000 which would suit you just fine unless you're doing a lot of 3d gaming.

The other option is to just bite the bullet with optimus and wait for support to arrive a year or so down the road.

---

### Post by 3Miro on 2011-10-10
> **drawkcab said:**
> 
Nvidia sans optimus can be had but beyond your price range unless you want to go lower end so that there really isn't much of an advantage over the Intel 3000.

Actually I was looking for low end Nvidia like 520-540, but everything below 560 is Optimus. While 560 is really powerful, it is very expensive and battery life is an hour tops.

> 
I bet you could find a really nice Lenovo thinkpad with AMD/ATI (the newer stuff runs just fine) or Intel 3000 which would suit you just fine unless you're doing a lot of 3d gaming.

I have only used ATI graphics on a desktop. The FOSS driver works great for anything other than wine-gaming, but for wine-gaming you want Nvidia. For work, FOSS ATI is perfect, except on a laptop, where you need proprietary drivers for good battery life. I've had very bad experience with proprietary ATI drivers on the desktop, but millage varies greatly. If you go for ATI, you should look for a way to test the system before you buy it.

> 
The other option is to just bite the bullet with optimus and wait for support to arrive a year or so down the road.

If you plan on using Linux, I wouldn't buy hardware with the hope of drivers eventually being released. So long as Linux people keep on buying Optimus, Nvidia has zero incentive to actually make drivers. It is my money for their driver and they are not getting a cent until they can deliver.

Sandy Bridge (i.e. HD 3000) has its own set of problems. I tried Xubuntu 10.10 and it won't even boot from the liveCD. Anything prior to 11.04 (or generally Linux before 2.6.37) won't work, but at least the newer versions are fine. I can even run smooth KDE, something that I couldn't do with the older Intel GMA 4500.

---

