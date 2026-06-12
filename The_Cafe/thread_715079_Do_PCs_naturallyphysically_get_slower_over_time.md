---
title: "Do PCs naturally/physically get slower over time?"
date: 2008-03-04
forum: The Cafe
---

### Post by Mazza558 on 2008-03-04
....or is it simply due to newer PCs being introduced to the market, and bloatware slowing things down (e.g newer versions of a program are bigger). 

I believe it's the latter, as IIRC, as hardware wears out, it'll suddenly stop working, not slow down.

---

### Post by Whiffle on 2008-03-04
Correct, they don't "slow down."  My 1.6GHz pentium 4 is just as fast now as it was 6 years ago when I built it.  Transistors either work, or don't work.

One thing that makes a difference though is our perception of speed.  My desktop feels fast, until I use my laptop.  My laptop isn't a whole lot faster (1.86GHz pentium M), but it feels like it runs circles around the desktop, even though its got slower hard drive transfer rates.  Its all relative.

---

### Post by hessiess on 2008-03-04
it feels fast untill you haft to use windows

---

### Post by k2t0f12d on 2008-03-04
Any real slowdown in the function of a PC is completely due to inefficiency and bugs in its software.  The registry in Microsoft Windows is one such culprit causing this kind of phenomenon.  Memory leaks are another.  Memory is "leaked" when it is still being reported as "in use" after the program that allocated has terminated.  Once a sufficient amount of memory has "leaked" and no longer usable by new processes, the system will become incrementally less responsive, or hang entirely.  Disconnecting power from the computer for 10 to 15 seconds and then rebooting will invariably treat the problems caused by leaked memory, but will not correct the bugs in the programs that caused it.

---

### Post by klange on 2008-03-04
Most hardware either works or doesn't, the only exception I know of is flash memory and power supplies. Flash memory will start having corruption (but not completely fail) if you write to it too many times. Power supplies corrode and start to lose effective output, but only after a few years.

---

### Post by k2t0f12d on 2008-03-04
The biggest problem I have with power supplies are their shoddy plastic mickey mouse fans burning out.  As far as actual output, I haven't ever had the need to test that.

---

### Post by Whiffle on 2008-03-04
Power supplies tend to loose their ability to accurately regulate their voltages, for example causing the +12V rail to be more like +12.5V.  Some devices don't care, but others do and that can cause hard lockups usually, along with other weird behavior.

---

### Post by klange on 2008-03-04
> **k2t0f12d said:**
> The biggest problem I have with power supplies are their shoddy plastic mickey mouse fans burning out.  As far as actual output, I haven't ever had the need to test that.
I have an 4 year old 300 watt that only puts out around 200. It used to be able to handle extra things like my x800, now it doesn't. Ditched it, got a new 500 watt, and now I'm back in business.

---

### Post by popch on 2008-03-04
Ageing hardware could conceivably slow down a PC.

As fixed disks become older, some sectors might require several trials until the PC succeeds in correctly reading a sector. I could imagine that the heat transfer paste on the CPU might become brittle and flake off, though I have yet to see such a thing. That might cause the CPU to throttle down.

> **k2t0f12d said:**
> Any real slowdown in the function of a PC is completely due to inefficiency and bugs in its software.  The registry in Microsoft Windows is one such culprit causing this kind of phenomenon.

Very true. There also might be an increasing number of programs being started in the background as well as an ever growing number of plugins, e.g. in the Windows Explorer, which can brake your system something wonderful.

> **k2t0f12d said:**
> ...Disconnecting power from the computer for 10 to 15 seconds and then rebooting will invariably treat the problems caused by leaked memory...

Simply restarting Windows will reclaim all leaked memory. There's no need to wait before rebooting. Upon restarting Windows, all memory allocation is done from scratch.

---

### Post by LaRoza on 2008-03-04
Hardware should function the same assuming it is not damaged.

RAM can be slowly damaged over time (cosmic radiation, mostly), and doesn't do a hard fail, but a soft fail, which can be tricky to diagnose.

Assuming there is no breakdown of the hardware, it should be the same at all times.

Software on the other hand will cause a computer to slow down as it changes. This will be different from various operating systems and configurations.

---

### Post by klange on 2008-03-04
> **popch said:**
>  I could imagine that the heat transfer paste on the CPU might become brittle and flake off, though I have yet to see such a thing

It happens. It happened to my desktop (the same one with the aging PSU). It had a destructive but not fatal effect on the CPU.

---

### Post by regomodo on 2008-03-04
> **WindowsSucks said:**
> Flash memory will start having corruption (but not completely fail) if you write to it too many times. 

no, no, no! Sorry, one of my masters assignments was about the physics/electronics of Flash.

---

### Post by KiwiNZ on 2008-03-04
There can be a slow down caused by material deterioration. In particular copper. Over time that can begin to crystalize and as a result impedence is increased.

---

### Post by aaaantoine on 2008-03-04
> **k2t0f12d said:**
> Memory is "leaked" when it is still being reported as "in use" after the program that allocated has terminated.

To be more technical, a memory leak is created when a memory pointer is given a new address to point to, without first clearing the memory at the original address.  

Assuming the OS properly handles the memory used by an application, the leak will be cleared up once the program is terminated.  Linux does this.  I wrote a simple C++ program to experiment with the idea, and posted the source code elsewhere on the forums.

The only time you have to reboot is if you can't individually restart the app that's causing the leak, such as if it's the kernel or a low-level process.

---

### Post by Zeroangel on 2008-03-04
Its due to feature creep as well as inefficient software (people generally go with how much they can get away with -- 4MB of extra RAM usage isnt a big deal to developers who have a gig of ram or more -- but it is a big deal to someone who only has over a hundred megs).

Speaking of -- I know someone who still uses Windows 98 on 128MB of PC100 RAM, and his PC is extremely quick!

---

### Post by klange on 2008-03-04
> **regomodo said:**
> no, no, no! Sorry, one of my masters assignments was about the physics/electronics of Flash.
Really? Writing too many times to an SD card makes it unusable. This is a known fact and is what makes using my SD card as swap space unfeasible.

---

### Post by fwojciec on 2008-03-04
> **KiwiNZ said:**
> There can be a slow down caused by material deterioration. In particular copper. Over time that can begin to crystalize and as a result impedence is increased.

This may very well be true about copper - I'm not an expert - except, as I understand it, the speed and performance of computers is not a function of the physical properties of the materials used in their construction but are determined, instead, by the frequency of the clock.  Computers are, in other words, digital not analogue devices.

---

### Post by popch on 2008-03-04
> **fwojciec said:**
> the speed and performance of computers is not a function of the physical properties of the materials used in their construction but are determined, instead, by the frequency of the clock.  Computers are, in other words, digital not analogue devices.

That is a common misunderstanding. We certainly think of the computer as digital because it is built to perform its functions that way. In fact, until the computers are made of some kind of quantum devices, they largely remain analog devices yielding results which we choose to interpret as being digital.

That point would remain for most practical purposes utter theory and perfectly irrelevant.

Since this thread is about possible influences of a computer's age on its performance, that distinction might be worthwhile to make.

There have as yet been named several possible causes for the deterioration of a computer's performance with increasing age, such as throttling the CPU because of thermal effects or increasing time needed for recovering errors in the hard disk drive.

Should the impedance of parts of the motherboard change over time, this might seriously impair the form of the signals transmitted, which in turns might force the system to throttle other components or to spend more time recovering errors. 

While such effects can conceivably happen, I have no way of knowing if there are observable instances where they in fact do happen.

---

### Post by futureproof on 2008-03-04
I'm by no means an expert but I have only experienced a hard disk slow down and eventually fail, don't know the cause.  How quickly does memory get cleared, I was reading 

[http://forums.speedguide.net/showthread.php?t=237786](http://forums.speedguide.net/showthread.php?t=237786)

and was suprised.

---

### Post by Zeroangel on 2008-03-04
> **WindowsSucks said:**
> Really? Writing too many times to an SD card makes it unusable. This is a known fact and is what makes using my SD card as swap space unfeasible.
Yeah, the physical properties of flash memory are set up so that whenever a write is done, electrons are pushed through a resistive surface and stuck there (signifying a 1), and when they are pulled back through the resistive surface to change it to a 0. Each time an electron is pushed through the membrane, it wears the membrane down a little bit. With flash memory, it does experience wear during each write because pushing electrons through resistive surfaces eventually wears the surface down.

RAM is works differently, and it is generally understood that it can last for decades and sustain billions of writes rather than just thousands.

Technologies such as readyboost (which use your thumbdrive as swap space) do wear down flash drives, however they do it smartly, distributing the writes through the available surface of the drive rather than writing in the same area over and over.

Luckily flash memory is cheap these days and can only get cheaper.

Another bit of trivia -- defragging flash drives is useless because they have no seek time unlike hard disks. The seek is near instantaneous :)

---

### Post by macogw on 2008-03-04
One thing I've seen that can slow one down that can be attributed to time is the buildup of dirt/dust.  If the heatsink is packed with dirt, some processors (Pentium 4's for certain) will scale down dramatically to keep from overheating.  I'd estimate, based on how slow the computer I saw do this was, that they can scale down below 300MHz (it was slower than my 300MHz Pentium II).

---

