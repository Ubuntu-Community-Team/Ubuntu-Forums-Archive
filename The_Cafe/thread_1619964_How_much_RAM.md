---
title: "How much RAM?"
date: 2010-11-12
forum: The Cafe
---

### Post by weasel fierce on 2010-11-12
How much RAM do you consider enough for ubuntu?
By "enough" I mean to have a reasonable, pleasant experience and meet your daily needs. Elaborate as required.

---

### Post by scouser73 on 2010-11-12
I have 1Gb of RAM, I think that it does what I need and i have a good user experience.

---

### Post by XubuRoxMySox on 2010-11-12
512 runs Xubuntu (minus PulseAudio, using ALSA instead) very nicely.

-Robin

---

### Post by Dr. C on 2010-11-12
It really depends on what one wants to do with Ubuntu. For basic web browsing word processing etc. 1GB is more than enough and one can get away with 512 MB. I have installed Ubuntu 6.10 and 7.04 on as little as 192 MB. On the other hand, if one is into running multiple virtual machines, compiling operating systems, running a busy server the sky is the limit.

---

### Post by weasel fierce on 2010-11-12
My old machine (up to 8.something) had 768 megs which ran pretty well. It started with 256 which worked but was a bit sluggish.

My current machine is 4 gigs, which runs great for most purposes.

---

### Post by andymorton on 2010-11-12
My netbook (HP Mini 110) has 1GB RAM and runs Ubuntu Desktop Edition perfectly well. There isn't a noticeable difference between that and my laptop which has 2GB.

---

### Post by czr114 on 2010-11-12
When desktop RAM shortages used to be more common than they were now, the average user was swapping regularly during the course of normal activities. So, in defining these floors

I'd consider 1GB to be a general floor for avoiding the swap bottleneck during the course of normal activity. 1.5GB would be good on a 64-bit OS or when using the preload daemon. Those numbers assume well-pruned background processes and a lack of docks, heavy theming, notification applets, desktop widgets, and the like. That also assumes that certain periodically-used applications, such as Thunderbird, are invoked as needed, and not left running in the background That also assumes that certain applications, such as Firefox, are run with memory-efficient configurations, which in the case of Firefox, would involve use of AdBlock Plus.

512MB can be workable for limited-purpose workstations, such as those found in a school computer lab. With good tuning, 512MB won't cause too many swap headaches for those making well-focused use of productivity software. It won't however, be sufficient for those working with graphics, presentations, or aggressively multi-tabbing in a web browser.

---

### Post by LMP900 on 2010-11-12
I have 8GB installed on my desktop. It's mainly for running virtual machines, although I should have paired it with a larger hard drive. I would actually be satisfied with a netbook that only had 1GB of RAM, provided that it had a full-size keyboard.

---

### Post by Paqman on 2010-11-12
1GB runs Ubuntu fine. You can make it run better if you have more by fiddling about with swappiness, preload, ramdisks etc, but it's prefectly good with 1GB.

---

### Post by 3Miro on 2010-11-12
Only on very rare occasions have I seen Ubuntu go over 1GB of RAM (when I am not playing wine games or using some math related software). 2GB will be enough even for that.

The good news for Linux is that even if you have extra RAM, it will not be wasted, but rather used as HDD cache. I have 3GB on my laptop and 4GB on my Desktop, but soon I will upgrade the desktop to 8GB.

---

### Post by weasel fierce on 2010-11-12
seems consensus so far is a gig is fine, but a bit more can't hurt.

---

### Post by Khakilang on 2010-11-13
512MB is bearable, 1GB is fine and 4GB will be ideal. But I only use 1.5GB since I manage to salvage 512MB from other computer.

---

### Post by chessnerd on 2010-11-13
1 GB is plenty for Ubuntu.

You can get away with 768 MB, but I wouldn't suggesting going down to 512 MB. The experience is less than enjoyable, as I found out on my older desktop.

Not counting cache, I rarely go above 768 MB on my laptop. With cache, I generally sit around 0.75-1.25 GB (but I do sometimes see the cache get over 2 GB if I've been using the computer for a few hours).

---

### Post by mips on 2010-11-13
1GB is OK but more ram can never hurt. Sweet spot for me is 4GB.

---

### Post by chessnerd on 2010-11-13
> **mips said:**
> 1GB is OK but more ram can never hurt. Sweet spot for me is 4GB.
It is true that more RAM never hurts, but it doesn't help on a system which exceeds 4 GB while using a 32-bit OS (unless this 32-bit OS is using [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension"), in which case, it varies... Ex. for Linux, you'd need to go beyond 64 GB) or when the motherboard and/or CPU does not offer support for more RAM. But yes, other than your pocketbook taking a hit, it doesn't hurt to have more RAM on hand.

That being said, there is such a thing as overkill. I'd never get more than 6 GB of RAM for a desktop system running Ubuntu 10.04 because, frankly, I'd never use it all. Even 4 GB is pushing it for the average user of Ubuntu. However, you may not be an average user in that regard.

On the other hand, though, there's no kill like overkill... ;)

---

### Post by bcschmerker on 2010-11-13
My hybrid Everex®, currently equipped with a Gigabyte® MA78GM-S2HP, Advanced Micro Devices® Athlon X2 5600+ (Socket AM2), and Creative Laboratories® SB0350 PCI audio card (CA0102 chipset), running Ubuntu® 10.04-LTS Lucid, gets by with 2 GB total, including 128 MB for the onboard ATI Radeon HD3200 video display chip; rarely does it push 1 GB active memory in practice to date (as of 13 November 2010).  Advance plans call for 8 GB ECC registered to accompany an MPU upgrade to an Advanced Micro Devices® Athlon II X4 or Phenom X4 (Socket AM3), as I may very well need the additional RAM for all the processes a quad-core can sequence, with an AMD®-based PCI-Express X16 video-adapter card as a further contingency.

---

### Post by simpleblue on 2010-11-13
My 1300Mhz laptop runs great on 1gb. I've only had one occasion in which I went into swap, and at that time I was pushing the OS's limits on purpose. I had several videos on at once and was streaming as well. This is beyond what a regular user does.

Perhaps instead of wasting money on extending ram, a person could consider getting an solid state HD.

---

### Post by mips on 2010-11-13
> **chessnerd said:**
> It is true that more RAM never hurts, but it doesn't help on a system which exceeds 4 GB while using a 32-bit OS (unless this 32-bit OS is using [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension"), in which case, it varies... Ex. for Linux, you'd need to go beyond 64 GB) or when the motherboard and/or CPU does not offer support for more RAM. But yes, other than your pocketbook taking a hit, it doesn't hurt to have more RAM on hand.

That being said, there is such a thing as overkill. I'd never get more than 6 GB of RAM for a desktop system running Ubuntu 10.04 because, frankly, I'd never use it all. Even 4 GB is pushing it for the average user of Ubuntu. However, you may not be an average user in that regard.

On the other hand, though, there's no kill like overkill... ;)


I use 64-bit so i'm not worried about the 32-bit barrier.

Just yesterday I used all 4GB of my RAM so it's not wasted :D

---

### Post by handy on 2010-11-13
I've been using one machine with 2GB & the iMac with 1GB. I don't use /swap on either machine.

I will be doing a lot of work with Lightview 3, under OS X, soonish, so I might boost this thing up to this iMac's max of 4GB whilst the Oz dollar is strong.

---

### Post by Goldfissh on 2010-11-13
Anywhere from 1GB upwards is brilliant, I think. That said, you can easily run Ubuntu on much lower levels of RAM, as you already established. I think it comes down to matter of preference and what you use your machine for, really.

---

### Post by mips on 2010-11-13
> **handy said:**
> I've been using one machine with 2GB & the iMac with 1GB. I don't use /swap on either machine.


I've actually never tried turning my /swap off before, think it's about time.

---

### Post by zer010 on 2010-11-13
Personally, I'd say around 1GB - 2GB, but it wasn't one of the options... I'm running with 1.5GB and everything I use Ubuntu for runs quite smoothly. I don't think I've ever really used any of my over-sized 1GB swap space. :P

---

### Post by Sylos on 2010-11-13
Varies on requirements:

I have 2 desktops. The main one runs ubuntu normal and studio on a 2ghz AMD Athlon processor. I was running with 1g RAM until fortune recently intervened and killed a 512mb stick which I replaced with an old 256mb stick. I havent actually noticed any problems with less under either distro - even running 12 tracks of audio in ardour DAW under Ubuntu Studio. 

My second desktop uses ubuntu Hardy (old schoolI know) I only use this one for playing movies when Im in bed). It has 384mb (i think - from memory) and runs just fine for that.

On a pentium III machine I did  for my dad he runs lubuntu 10.04 with 384mb RAM and that does what he needs. He only searches the web and use wordprocessor so the load is very little.

I guess the key question is "how patient are you?". 256mb and above will probabbly support a lightweith distro (depending on other hardware) but you may need to be patient when perfomring complex tasks.

---

### Post by Cabalbl4 on 2010-11-13
2+ GB is fine for me with simultaneously  enabled proftpd, linuxDC++, tor, Transmission, Virtualbox with 512 mb XP guest, playing 3D games in WINE, and a ton of other small useful services.
Usually it takes 1,5 GB without using much SWAP.

---

### Post by handy on 2010-11-13
> **mips said:**
> I've actually never tried turning my /swap off before, think it's about time.

I kept an eye on it for a while with htop, & noticed that I never use it. So I deleted the /swap partition on the iMac & I don't think I've had one on the No.2 box (2GB RAM) for well over 4 years.

Though as previously stated, I'm going to be using Lightroom some, & it recommends 2GB minimum for OS X. So whilst the prices are good & the dollar up, it seems like the right time.

---

### Post by Sean Moran on 2010-11-13
This little Compaq CQ60 laptop came complete with 2Gb RAM if I recall my figures rightly (I hardly ever need to venture into Setup so it is testing my powers of recall a tad), yea but I've had Karmic running on a Pentium II Deskpro with 160Mb RAM a few months ago, and there are noticable delays with the mouse-cursor movements fairly frequently, but it still gets up and runs more responsively than WinXP runs its mouse-cursor on this machine with more RAM than any sensible desktop really needs for browsing the web and raving on Skype and such.

Put simply, Ubuntu runs more responsively with 160MB than XP does with 2Gb.

---

### Post by wkhasintha on 2010-11-13
It depends , x >= 1024 MB (where x=amount of memory in MBs) is decent enough to run an Ubuntu 10.** system smoothly with Compiz-fusion .

---

### Post by c00lwaterz on 2010-11-13
i think it depends if lxde, edubuntu, kde or gnome. but i think for general use with games maybe 2 to 3 gb for casual gamer. if 4gb above maybe for graphics work and audio work. just my opinion. :popcorn:

---

### Post by Nightstrike2009 on 2010-11-14
I have 4Gb of memory (or 3.5Gb has my PC sees it), this was only because my PC is new this year. With older PC's 1-2Gb should probably be fine.

My Graphics card also has 1Gb of ram to itself, Linux has always worked fine on my PC.

---

### Post by MasterNetra on 2010-11-14
Have only my 1GB of ram on my laptop. Would like 4GB for gaming & Virtual machines, but meh. The 1GB though is more then enough for casual use though.

---

### Post by bcschmerker on 2010-11-17
> **chessnerd said:**
> It is true that more RAM never hurts, but it doesn't help on a system which exceeds 4 GB while using a 32-bit OS (unless this 32-bit OS is using [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension"), in which case, it varies... Ex. for Linux, you'd need to go beyond 64 GB) or when the motherboard and/or CPU does not offer support for more RAM....

That being said, there is such a thing as overkill. I'd never get more than 6 GB of RAM for a desktop system running Ubuntu 10.04 because, frankly, I'd never use it all....

On the other hand, though, there's no kill like overkill... ;)In fact, my own advance plans have another contingency for a return to the AMD64 edition, the condition being full Adobe Systems support for 64-bit Flash (experimental as of 16 November 2010, the previous 64-bit full support being terminated with Version 10.0.45.2 due to multiple critical bugs).  Both 32- and 64-bit versions of Mozilla Firefox 4.0 should be able to handle W3C Hypertext Markup Language 5.0 from the outset, with an Extension to retrofit it to Firefox 3.6 pending.

---

### Post by Rasa1111 on 2010-11-17
I have 1 gig and it is more than enough for any Ubuntu i throw at it.
I guess 2 would be even sweeter, but 1 is definitely plenty on this old box.
lol

my dad only has 512 mb RAM on his computer, 
and his runs ubuntu perfectly to.
I do notice it a bit slower, and he does have a better/faster processor than me, SO I think it is best to have 1 GB of ram at least.
even though 512 will run it fine if you must.

 I also have put Ubuntu on his wifes PC, 
and my mothers PC..
and they each have only 512 MB as well. 
but they run great. 

I still feel better with at least one gig though.. lol :P

 Oh, but my a friend has a bit over 5 GB RAM, Ubuntu 10.04
 and that is more than the PC ever uses, and probably more than it ever will use. :lol:

---

### Post by Version Dependency on 2010-11-17
I have 6 gigs...but for it's certainly more than necessary.  My sister runs Ubuntu with 4 gigs RAM and is just as quick.  My mother runs Ubuntu on 2 gigs and is noticeably slower, but not extreme. I have used Ubuntu on an older PC with only 1 gig and it ran OK...wasn't slow by "Windows standards"...but a bit slow in terms of Linux.  But still usable. I've tinkered with less than 1 gig a bit...and I didn't really like the results.

---

