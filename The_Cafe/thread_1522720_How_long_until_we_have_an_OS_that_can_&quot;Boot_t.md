---
title: "How long until we have an OS that can &quot;Boot to Cache&quot;"
date: 2010-07-02
forum: The Cafe
---

### Post by chessnerd on 2010-07-02
Plenty of Linux distros offer an option to boot into RAM, but as CPU cache amounts increase, how long will it be before a minimalist distro can boot completely and run totally inside the CPU caches?

Would such a thing even be possible?

---

### Post by McRat on 2010-07-02
Have one core work on the BIOS tests.

Have another start loading the O/S into cache from 2gb worth of SSD chips on a PCI board/daughter board.

Since the BIOS is testing the HDD and memory, you'd have to separate the two?

The instant the BIOS is done, the O/S will launch in millisecs.

---

### Post by eltonw on 2010-07-02
> **chessnerd said:**
> Plenty of Linux distros offer an option to boot into RAM, but as CPU cache amounts increase, how long will it be before a minimalist distro can boot completely and run totally inside the CPU caches?

Would such a thing even be possible?

Isn't that what happens when you run ubuntu or other distro as a "Live CD"? IMVHO, everything runs in RAM, or is something written to the HD? ... perhaps the temporary swap?

---

### Post by V for Vincent on 2010-07-02
Don't think it could ever be worth it, so for a modern OS my guess is never. As for something from 20 years ago, sure...

---

### Post by V for Vincent on 2010-07-02
> **eltonw said:**
> Isn't that what happens when you run ubuntu or other distro as a "Live CD"?

What the OP means is a really tiny cache located directly on the CPU, which is much faster than RAM but far more expensive.

---

### Post by chessnerd on 2010-07-02
> **eltonw said:**
> Isn't that what happens when you run ubuntu or other distro as a "Live CD"? IMVHO, everything runs in RAM, or is something written to the HD? ... perhaps the temporary swap?

When it runs as a Live CD the CD acts as the hard drive, there is no swap space, and all the running programs run in RAM like normal.

Some LiveCD distros offer to load all programs into RAM while they boot, this allows programs to open almost instantly because they are already in RAM.

What I am talking about is the CPU cache, ie the L1, L2, and L3 caches located inside the CPUs of the computer. There is generally only a few MB of space in those caches, and they are used by the CPU to store information currently being worked on. As time goes on, these caches will get larger. My question is, would it even be possible to load an operating system into them so that programs and processes are always being run by the CPU. Everything would be done inside the processor itself.

With RAM speed increasing this really isn't necessary, but I do think that it would be interesting for a distro to try to do that.

---

### Post by McRat on 2010-07-02
Yeah, those caches are getting pretty big. 6mb?  12mb?
 
I doubt if the most frequently called API's in a modern O/S are 6mb.  
 
But I suppose the question is, are they already doing it?  Are the most common O/S subroutines already sitting in cache in a new computer?
 
I really believe that RAM as we know it will disappear in 5-10 years.  A combination of larger cache, more cores, and SSD technology will eliminate RAM and HDD's.  The SSD will have partitions for each core, then one for long term storage, and SSD data/instructions will be moved directly into cache.

---

### Post by Lucradia on 2010-07-02
> **McRat said:**
> Yeah, those caches are getting pretty big. 6mb?  12mb?

Harddrive cache is also getting unbelievably big... I've seen some with 64 MB.

Also, threads aren't cores.

So if you have an Intel core i7 with 4 cores (8 threads total) then it's only 4 partitions, even though GNOME says there are 8 cores, which is wrong.

---

### Post by earthpigg on 2010-07-02
FreeDOS was the first thing that popped into my head after reading OP.

we're approaching a point wherein the cache of common CPU's is larger than the full size of DOS 6.22.

---

### Post by McRat on 2010-07-02
> **earthpigg said:**
> FreeDOS was the first thing that popped into my head after reading OP.

we're approaching a point wherein the cache of common CPU's is larger than the full size of DOS 6.22.

It's already past that point.  The actual O/S of DOS 1.x-6.x never exceeded about 130k IIRC.  The rest of the disk(s) content was utilities.

DOS ran in 640k including applications.  MS Drivers (Expanded and Extended RAM) and aftermarket libraries would permit up to about 16 MB IIRC, but that was it, total O/S, code, and data.

---

### Post by donkyhotay on 2010-07-02
> **McRat said:**
> It's already past that point.  The actual O/S of DOS 1.x-6.x never exceeded about 130k IIRC.  The rest of the disk(s) content was utilities.

DOS ran in 640k including applications.  MS Drivers (Expanded and Extended RAM) and aftermarket libraries would permit up to about 16 MB IIRC, but that was it, total O/S, code, and data.

I remember manually tweaking the amount of RAM used by DOS with EMM386. It wasn't much but shaving off 1kb or two of RAM normally used in my various peripherals like the mouse, keyboard, monitor, etc. would often make big differences in what games I could run at the time when my entire system only had 2mb of RAM. Now even if I could remember how to do that stuff it wouldn't make any difference since I'm running a couple GB's of ram and a couple of KB's would make no difference.

---

### Post by McRat on 2010-07-02
> **donkyhotay said:**
> I remember manually tweaking the amount of RAM used by DOS with EMM386. It wasn't much but shaving off 1kb or two of RAM normally used in my various peripherals like the mouse, keyboard, monitor, etc. would often make big differences in what games I could run at the time when my entire system only had 2mb of RAM. Now even if I could remember how to do that stuff it wouldn't make any difference since I'm running a couple GB's of ram and a couple of KB's would make no difference.

Yes, if your program needed 512k free to run (common), and you had any drivers loaded, there wasn't 512k left afterwards.  So you put drivers up in the HMA (High Memory Area) between 640k-1024k using EMM386.  Before that, there were LOAD switches you had to do /X? when loading the device drivers on the 8088-80286 machines?

Back then, you REALLY needed to know how to tweak your CONFIG.SYS and BIOS to get the most out of your machine.

Tech support was a nightmare though.  Imagine taking a normal person today and try to walk them through editing their CONFIG.SYS file via just a telephone call.

---

### Post by schauerlich on 2010-07-02
If the OS fits into cache, it will probably mostly be there anyways - the CPU manages the cache and keeps frequently references sections of memory handy. It would still be syncing the cache with RAM, which would be a slow down. However cache management is done in hardware, so you'd need a new chip to work entirely from the cache.

---

### Post by mickie.kext on 2010-07-02
> **chessnerd said:**
> Plenty of Linux distros offer an option to boot into RAM, but as CPU cache amounts increase, how long will it be before a minimalist distro can boot completely and run totally inside the CPU caches?

Would such a thing even be possible?

That is pretty much impossible with x86. CPU cache is not exposed to operating system, it is managed by on-chip scheduler and pre-fetcher which drags stuff from RAM to cache.

It is posible for some databases to use cache more frequently, but for OS to be loaded in cache... I don't think it is possible.

---

### Post by SagnaB on 2010-08-01
I'm sure someone in Military technology development could answer this question; Lockheed Martin or something.

Pitty I am no such parson...


PS. on the topic of Lockheed Martin (I know it's slightly off topic to this thread) but, does anybody else find LM's company slogan "We never forget who we're working for", a tad strange/creepy?

---

### Post by Dustin2128 on 2010-08-01
With a 64Mb cache, you could load SliTaz, it only takes about 35Mbs if I recall correctly.

---

