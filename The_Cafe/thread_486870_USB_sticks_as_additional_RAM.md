---
title: "USB sticks as additional RAM"
date: 2007-06-28
forum: The Cafe
---

### Post by JC_510 on 2007-06-28
Hi,

I read an article recently that says that Vista has a feature that lets you use a USB memory stick as additional RAM. I am not too sure how it works, but I know it requires some software. EDIT: [Here is a link to Vista magazine, detailing the system.]("http://www.windowsvistamagazine.com/US/05582469248596696351/use-any-usb-stick-to-readyboost-your-computer.html")

Does anybody know if Ubuntu has a similar program?

---

### Post by Steveway on 2007-06-28
You can format the stick as a Linux-Swap Partition.
But it's better to use a partition on your harddisk, since it's much faster than a stick.
That's nothing new from Vista, they just say so.

---

### Post by starcraft.man on 2007-06-28
This USB stick RAM is **not** a substitute for actually having RAM though, nor is it better or faster than having Physical RAM slotted in the machine. It is a cheap substitute (for those who have those 1-4 GB flash pen drives) to marginally (haven't seen benchmarks, I suppose depends on how much base RAM your Vista system has) improve performance with VIsta, which is a system hog due to its RAM caching technique. 

IMO, Linux doesn't need this technology, unlike Vista we run on lower end systems with little performance depreciation.

---

### Post by kamaboko on 2007-06-28
It's called "Readyboost".  It's not meant to be a substitute for stick memory.  On the other hand, if you have a USB stick that's sitting around and not being used, toss it on there.  I threw a 512MB USB stick I wasn't using.  I didn't notice a lot of diff b/c my machine as it is is fast as hell.  I think it's interesting in that we will be moving away from conventional hard drives and toward flash drives in the future.

---

### Post by JC_510 on 2007-06-28
Yeah, I know it wont be as fast, I just wondered if the tech was available on Linux (course it is!!)

Ive got a 1gb flash drive that i dont use all that much, so i might give it a try

Thanks

---

### Post by starcraft.man on 2007-06-28
> **kamaboko said:**
> It's called "Readyboost".  It's not meant to be a substitute for stick memory.  On the other hand, if you have a USB stick that's sitting around and not being used, toss it on there.  I threw a 512MB USB stick I wasn't using.  _I didn't notice a lot of diff b/c my machine as it is is fast as hell._  I think it's interesting in that we will be moving away from conventional hard drives and toward flash drives in the future.

Well isn't that a kind of pointless feature then? From everything I've seen most people who know about Vista are buying it on newer machines that are more than capable of supporting Vista without any RAM increase from this. Other people who do have older machines and are keeping them aren't upgrading because the increased requirements, especially in graphics card just to run don't justify it. This ReadyBoost certainly doesn't help you if your CPU/Graphics card is too low end to support Vista at its fullest.

IMO, it just seems like a useless feature. Oh and as for the Flash Drive being future... I've yet to see that happen in a substantial way, call me sceptical.

---

### Post by PatrickMay16 on 2007-06-28
AGH!!!!!!!!!!! You can set up yourself a swap partition on your USB stick, and I can tell you that you won't experience any difference for it. If you have one GB of RAM, you could probably go without a swap partition at all. On my computer with 1.5GB of RAM, I never see any swap used with UBUNTU DAPPAR DRAKE.

---

### Post by saulgoode on 2007-06-28
My understanding is that the big benefit of ReadyBoost is storing large system files that are needed during bootup. It is probably quite useful for reducing the length of the Vista bootup cycle. Such an approach would probably improve Linux boot times to some extent, but not as much it helps Vista (in my experience, the bottlenecks for Linux booting are more attributable to hardware detection than file loading).

---

### Post by starcraft.man on 2007-06-28
> **saulgoode said:**
> My understanding is that the big benefit of ReadyBoost is storing large system files that are needed during bootup. It is probably quite useful for reducing the length of the Vista bootup cycle. Such an approach would probably improve Linux boot times to some extent, but not as much it helps Vista (in my experience, the bottlenecks for Linux booting are more attributable to hardware detection than file loading).

I think your confusing technologies. One ReadyBoost technology as in the article pertains to USB pen drives and boosting operating performance (once your actually booted). The other technology I think you confused it with is the Hybrid Flash Drives (they are combination drives from what I read that house both a large Serial drive for data and a flash part to be used for storing boot files and loading up quicker, as you noted) that are supposed to come out some time and the Flash based bit will apparently reduce boot up times. I have yet to see benchmarks on the improvement of the hybrid drives. I do know, having a pen drive slotted in Vista for ready boost isn't the same as having a hybrid drive (else they wouldn't be making them obviously).

I boot up my linux box in around 25-30 seconds from a cold start, and I've none of that tech. I don't see a need for it.

---

### Post by kamaboko on 2007-06-28
> **starcraft.man said:**
> Well isn't that a kind of pointless feature then? From everything I've seen most people who know about Vista are buying it on newer machines that are more than capable of supporting Vista without any RAM increase from this. Other people who do have older machines and are keeping them aren't upgrading because the increased requirements, especially in graphics card just to run don't justify it. This ReadyBoost certainly doesn't help you if your CPU/Graphics card is too low end to support Vista at its fullest.

IMO, it just seems like a useless feature. Oh and as for the Flash Drive being future... I've yet to see that happen in a substantial way, call me sceptical.

If I were to be very finicky and time how fast my apps open and close, then yes, I could verify a difference in speed.  But when I'm talking a savings of 3 to 4 seconds for a particular application, I don't really care.  I'll leave you with some stats.  As for flash drives replacing hard drives....you can bank on it.  They're more reliable, take less power, and disburse less heat.  [http://news.com.com/2100-1041_3-6147032.html](http://news.com.com/2100-1041_3-6147032.html)  As with all technology, prices will come down with higher volume and streamlined production. 

Booting into Vista (Without Readyboost):
Attempt 1: 1:10
Attempt 2: 1:12

Booting into Vista (using Readyboost):
Attempt 1: 1:05
Attempt 2: 1:03

Outlook 2007, using a 1000 meg PST file (Without Readyboost):
Attempt 1: 8,35 sec
Attempt 2: 3,2 sec

Outlook 2007, using a 1000 meg PST file (using Readyboost):
Attempt 1: 7,95 sec
Attempt 2: 3,2 sec

iTunes (Without Readyboost):
Attempt 1: 9,40 sec
Attempt 2: 4,93 sec

iTunes (using Readyboost):
Attempt 1: 12,5 sec
Attempt 2: 4,9 sec

---

### Post by tehkain on 2007-06-28
USB sticks(most) have a read/write limit. They can only take some 10 thousand rewrites. So using it as ram would last about a day if it was actually being used(like the PC actually needed to access it alot).

---

### Post by Tundro Walker on 2007-06-28
There was a thread a while back talking about Flash Sticks and Flash drives...some folks wanted to move to using them solely instead of disk drives.  But, then the limitation of the flash stick came up, where it can only take so many writes (it can read infinite times, but you can only write to the sectors so many times...like hundreds of thousands of times, but its still a limit.)  For just loading a base OS or parts of an OS on it to read off of, it's no big deal (which is why Puppy Linux and DSL work so well off flash sticks...they don't constantly read-write to the stick).  But for using a flash stick like actual RAM, which constantly loads in and out data, you'd burn up the flash stick in short order.  (someone did the math, I think it would be like a day or something).

But, in the same thread, they also pointed out the [i-ram drive]("http://techreport.com/reviews/2006q1/gigabyte-iram/index.x?pg=1"), which basically takes RAM sticks and makes a "drive" out of it.  You can load an OS on it, and boot in like 2 seconds off it.  When you turn your comp off, as long as your comp is plugged in (and power supply switch isn't turned off), it'll draw enough power to keep the RAM loaded.  Even if you turn off the power switch and unplug the comp, there's a battery on the card to keep the RAM powered for a period of time (like a couple hours or so).

Only problem is, it's a really expensive "drive".  You pay like $150-$200 for the card, then you have to buy the RAM to toss on it.  4 sticks of 1gb RAM can get kinda pricey.  Depending on how much you wanna pop, you could spend up to $400 on that bad boy.

But, if you really, REALLY want faster boot times...

---

### Post by starcraft.man on 2007-06-28
> **Tundro Walker said:**
> 
But, in the same thread, they also pointed out the [i-ram drive]("http://techreport.com/reviews/2006q1/gigabyte-iram/index.x?pg=1"), which basically takes RAM sticks and makes a "drive" out of it.  You can load an OS on it, and boot in like 2 seconds off it.  When you turn your comp off, as long as your comp is plugged in (and power supply switch isn't turned off), it'll draw enough power to keep the RAM loaded.  Even if you turn off the power switch and unplug the comp, there's a battery on the card to keep the RAM powered for a period of time (like a couple hours or so).

Only problem is, it's a really expensive "drive".  You pay like $150-$200 for the card, then you have to buy the RAM to toss on it.  4 sticks of 1gb RAM can get kinda pricey.  Depending on how much you wanna pop, you could spend up to $400 on that bad boy.

But, if you really, REALLY want faster boot times...

LOL thats not gonna take off any time soon, Vista certainly needs a lot more than just 4 GB for a base install with Office (default for lots of people). I mean the recommended amount on the partitioner I think is 23 GB at least, thats a lot of pricey Ram... if a card ever supports that much at once. IMO SATA is here to stay for a while, you raised an important limitation of Flash and until they find a way to improve or go around that they won't be selling lots of those.

---

