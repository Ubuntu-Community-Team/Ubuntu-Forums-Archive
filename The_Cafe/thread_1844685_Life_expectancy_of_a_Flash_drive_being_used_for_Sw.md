---
title: "Life expectancy of a Flash drive being used for Swap/ReadyBoost?"
date: 2011-09-15
forum: The Cafe
---

### Post by MasterNetra on 2011-09-15
I was wondering if anyone had any idea what the life expectancy of a flash drive would be if it was used for readyboost/swap? I have both a 8GB and 4GB flash drive I was thinking of using the 4GB as a Swap drive to further my system's performance capabilities for like gaming and what not, laptop only has 1GB of ram and supposedly can't be upgraded further (although when I had windows on this machine I had some hardware info software that said it could support up to 2GB and claimed that the bio's info or whatever on it was wrong, but dunno) so yea could use the boost. I've had both USB drives for about 3 or so years already.

---

### Post by disabledaccount on 2011-09-15
It depends on quality of flash chip and current life-time write count.
Generally Flash drive is not dedicated for write-intensive applications and for long term data holding, because it don't have spare "sectors" (unlike HDD) and is not protected by wear-prevention algorithms (unlike SSD).

---

### Post by MadCow108 on 2011-09-15
ssd's lasts years even if you write and read from them 24/7.

or are you talking about flash chips like their built in usb sticks? those probably last less long.

but making your swap faster will not gain you much, especially for gaming.
even on the best ssd io bandwidth and latency is several orders of magnitude slower than ram so your machine will still come to a grinding halt whenever you start swapping.

---

### Post by gordintoronto on 2011-09-15
Using a USB flash drive for swap will be much, much slower than using your hard drive.

---

### Post by MasterNetra on 2011-09-15
> **MadCow108 said:**
> ssd's lasts years even if you write and read from them 24/7.

or are you talking about flash chips like their built in usb sticks? those probably last less long.

but making your swap faster will not gain you much, especially for gaming.
even on the best ssd io bandwidth and latency is several orders of magnitude slower than ram so your machine will still come to a grinding halt whenever you start swapping.

> **gordintoronto said:**
> Using a USB flash drive for swap will be much, much slower than using your hard drive.

I see.

---

### Post by JustinR on 2011-09-15
If it's an expensive flash drive like [these]("http://store.sony.com/webapp/wcs/stores/servlet/CategoryDisplay?categoryId=27891&N=4294950465&catalogId=10551&storeId=10151&langId=-1&accessory=true"), they can usually go 1-3 million writes before they become read-only, and unwritable.

---

### Post by kerry_s on 2011-09-15
I used a flash drive as swap for a year, I still use that same drive no problem. 

With 1gb I wouldn't even use swap, but that's just me.

---

### Post by BeRoot ReBoot on 2011-09-15
> **gordintoronto said:**
> Using a USB flash drive for swap will be much, much slower than using your hard drive.

I think the OP's talking about SATA flash drives, or, as they're commonly referred to as, SSDs.

---

### Post by MasterNetra on 2011-09-15
> **BeRoot ReBoot said:**
> I think the OP's talking about SATA flash drives, or, as they're commonly referred to as, SSDs.

No, I am referring to your typical USB Flash Drives...Unless those are considered Sata, if so then thats news to me. >.>

---

### Post by BlacqWolf on 2011-09-15
> **MasterNetra said:**
> No, I am referring to your typical USB Flash Drives...Unless those are considered Sata, if so then thats news to me. >.>

SATA is a type of hardware interface/connector, commonly used for non-removable media like internal SSDs/HDDs. A USB flash drive... well, uses USB.

---

### Post by MasterNetra on 2011-09-15
> **BlacqWolf said:**
> SATA is a type of hardware interface/connector, commonly used for non-removable media like internal SSDs/HDDs. A USB flash drive... well, uses USB.

I know that. Which i why it would of been news to me if USB Flash Drives would of been considered Sata.

---

### Post by BlacqWolf on 2011-09-15
> **MasterNetra said:**
> I know that. Which i why it would of been news to me if USB Flash Drives would of been considered Sata.


Ok. I really couldn't tell if it was a joke or not. :lol:

---

### Post by MasterNetra on 2011-09-15
> **BlacqWolf said:**
> Ok. I really couldn't tell if it was a joke or not. :lol:

It was a little bit joke and a little bit sarcasm.

---

### Post by tgalati4 on 2011-09-15
Flash drives work fine until they d

---

### Post by boscharun on 2012-01-14
Feasibility of [using pen drive as RAM]("http://www.skipser.com/p/2/p/how-to-use-pen-drive-as-ram.html") depends on your usage. If its like you end up using swap daily, better go for RAM upgrade.
If it is like you use swap only occasional during heavy use, a pen drive can be a great alternative. You can even assign the flash drive as swap any time before the swap actually starts to get used as well.

---

### Post by del_diablo on 2012-01-14
If you have 8k of ram, you could "cheat" and setup a ramdisk as swap.
So perhaps you have 7 gigs of ram, and 1 gig of ram as "Fake cache".

---

### Post by mightyiam on 2013-03-03
I did real filesystem caching [like this]("http://randomcrystal.blogspot.co.il/2013/03/hybrid-ssdhdd-ssd-caching-using.html") (my blog).

---

### Post by 3rdalbum on 2013-03-03
Only do it if you don't mind junking the 4 gig stick.

I ran my server's operating system for six months on a Corsair Voyager flash drive. The last two months it was read-only due to the flash dying. At the end the stick was complete junk and could not be formatted.

I didn't have swap on the drive, but I can imagine using swap on a USB flash drive would probably turn it into junk quickly.

---

### Post by pqwoerituytrueiwoq on 2013-03-03
i had a generic 1gb drive fail after a week of running firefox off it

---

### Post by mightyiam on 2013-03-03
I used an SSD, not a USB flash drive. And there's a difference between swap and filesystem caching. ReadyBoost is filesystem caching. Ideally, you'd want to never use swap. Filesystem caching, however, is very useful.

---

### Post by kurt18947 on 2013-03-04
> **DawnLight said:**
> I used an SSD, not a USB flash drive. And there's a difference between swap and filesystem caching. ReadyBoost is filesystem caching. Ideally, you'd want to never use swap. Filesystem caching, however, is very useful.

You need swap and on a separate partition if you want to use hibernate (AKA suspend to disk).

---

### Post by mightyiam on 2013-03-04
Yes, you are right, kurt18947, but [Hibernation has been disabled by default since precise]("https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/812394") and I don't need it anyway. Besides, it still is true that you'd never want to use swap in the common sense that you never want to run out of memory. Sure - you want to set up swap just for hibernating - go ahead.

---

### Post by Paddy Landau on 2013-03-04
I once tried using a USB stick for this purpose, and it lasted about six months. After it failed, I realised that my system was no slower without it anyway! (That was with USB 2; I don't know how USB 3 would affect the system.)

Your best bet, if you can afford it, is to upgrade your RAM from your current 1Gb. If you have 64-bit Ubuntu, I recommend 4Gb or more for performance.

---

### Post by mightyiam on 2013-03-04
> **Paddy Landau said:**
> I once tried using a USB stick for this purpose, and it lasted about six months. After it failed, I realised that my system was no slower without it anyway! (That was with USB 2; I don't know how USB 3 would affect the system.)

Your best bet, if you can afford it, is to upgrade your RAM from your current 1Gb. If you have 64-bit Ubuntu, I recommend 4Gb or more for performance.

32 bit Ubuntu handles 4GB of RAM or more. It is called PAE.

---

### Post by Paddy Landau on 2013-03-04
> **DawnLight said:**
> 32 bit Ubuntu handles 4GB of RAM or more. It is called PAE.
Yes, I'm aware. It's just that 64-bit performs better with a bit more RAM than with 32-bit.

---

### Post by mJayk on 2013-03-04
> **Paddy Landau said:**
> Yes, I'm aware. It's just that 64-bit performs better with a bit more RAM than with 32-bit.


does it ?

---

### Post by Paddy Landau on 2013-03-04
> **mJayk said:**
> does it ?
I've been told that 64-bit needs a bit more RAM than 32-bit for the same performance. I could be wrong. Anyway, that's beside the point for the OP — upgrading his RAM by even 1Gb (if he can afford it) will do more for his performance than a USB stick, especially if it's USB 2.

---

### Post by Paqman on 2013-03-04
> **MasterNetra said:**
> I was thinking of using the 4GB as a Swap drive to further my system's performance capabilities for like gaming

If you're looking for improved game performance, you don't want to be swapping over USB. It'd be slooooooooowwwwww. As others have mentioned, you'd be much better off using your hard drive.

If you find your machine is chewing through RAM, you can increase the size of your internal swap. It's possible to permanently expand your existing swap partition, add new swap partitions, or add swap files, which can be done on the fly or on a temporary basis if you want.

[More info here]("https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F").

Obviously adding more swap runs a very, very distant second place to adding more RAM. However, that will depend on your hardware. Adding more RAM to a desktop is easy, adding it to laptops can range from easy to difficult to impossible. Modern RAM is pretty cheap, but some of the older stuff can be quite expensive. Second hand is good, try Ebay.

---

### Post by Paqman on 2013-03-04
> **del_diablo said:**
> If you have 8k of ram, you could "cheat" and setup a ramdisk as swap.
So perhaps you have 7 gigs of ram, and 1 gig of ram as "Fake cache".

?!?

Why would you reserve some RAM for use when you ran out of RAM? Just use the RAM as RAM, using it as swap is a bit mental. You can [reduce the swappiness]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F") of your machine so that it hardly touches swap, the default is way too conservative IMO. With 8GB RAM and swappiness=0 you'd be unlikely to ever need any swap at all. You could get by with a little bitty swapfile as a backup.

---

### Post by kurt18947 on 2013-03-07
> **Paddy Landau said:**
> I've been told that 64-bit needs a bit more RAM than 32-bit for the same performance. I could be wrong. Anyway, that's beside the point for the OP — upgrading his RAM by even 1Gb (if he can afford it) will do more for his performance than a USB stick, especially if it's USB 2.

My experience is that the system with a 64 bit O.S. will use about 100 MB. more RAM just in an idle state than with a 32 bit O.S. That said, I'm on a Core 2 duo with 2 GB. RAM no swap and for casual/office use have never had a low RAM issue running a 64 bit O.S. Right now System Monitor says I'm using 583 MB. RAM just running system monitor and firefox.  This is 13.04 64 bit. I don't have 13.04 32 bit for an apples to apples comparison but based on past experience, I'd expect a 32 bit install to be using 250-300 MB. RAM.

---

### Post by Paqman on 2013-03-07
> **kurt18947 said:**
> My experience is that the system with a 64 bit O.S. will use about 100 MB. more RAM just in an idle state than with a 32 bit

Sounds about right to me too.

---

