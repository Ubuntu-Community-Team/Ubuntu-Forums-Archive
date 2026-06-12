---
title: "SuperPI no go - how about System Stability Tester?"
date: 2010-01-18
forum: The Cafe
---

### Post by futz on 2010-01-18
[quote=powel212]For some reason super pi doesn't run in Karmic.[/quote]
[System Stability Tester]("http://systester.sourceforge.net") does the same thing, and more. So let's have a performance benchmark contest with SST instead of SuperPI. :D

I downloaded both the Version 1.1.0 amd64 and x86 binaries and ran them both to 1 million Pi digits with 1 thread, using the Borwein algorithm.

My CPU is an Intel Yorkfield Q9650 3GHz Quad Core. I'm running 4GB of Mushkin XP2-8500-Ascent RAM. I'm running Ubuntu 9.10 64-bit.

Here's a screenshot of the x86 run:
[ATTACH]143992[/ATTACH]

and here's a screenshot of the 64-bit run:
[ATTACH]143993[/ATTACH]

---

### Post by Psumi on 2010-01-18
Few, thought my computer was going to die for a moment there.

[[img]http://i50.tinypic.com/14y4bb7_th.png[/img]](http://i50.tinypic.com/14y4bb7.png)

---

### Post by futz on 2010-01-18
> **Psumi said:**
> Few, thought my computer was going to die for a moment there.
A couple sentences with hardware details would make your results more meaningful. :)

Like this:
[quote=futz]My CPU is an Intel Yorkfield Q9650 3GHz Quad Core. I'm running 4GB of Mushkin XP2-8500-Ascent RAM. I'm running Ubuntu 9.10 64-bit.[/quote]

I guess we should also mention which version of the SST program we're running.

---

### Post by Psumi on 2010-01-18
> **futz said:**
> A couple sentences with hardware details would make your results more meaningful. :)

IBM T41 --
-- 512 MB of RAM (496 MB Usable) Unknown Maker
-- Pentium M Centrino Single (NON-HT compatible) Core 1600 MHz Processor
-- 32 MB Video RAM

> I guess we should also mention which version of the SST program we're running.

My Version is listed at the top of my screenshot.

---

### Post by futz on 2010-01-18
> **Psumi said:**
> My Version is listed at the top of my screenshot.
I meant whether you're using the x86 or 64-bit version. :)

---

### Post by Marvin666 on 2010-01-18
It took 58.705s See signature for hardware specs.

---

### Post by Rhubarb on 2010-01-18
yay!

Thanks for letting me know of SST, as superpi seems to be borked in Ubuntu 9.10.

My system specs:
Intel Core i7 975 Extreme @ 3.33GHz (not overclocked)
Corsair 6GB DDR3 (3 x 2GB 1333MHz sticks)
Ubuntu 9.10 64-bit

I think I'll experiment with overclocking now that I've got a suitable benchmarking app (the phoronix test suite is fine, but isn't user-friendly to install and use).

---

### Post by PurposeOfReason on 2010-01-18
25.49 seconds with a i5 at 2.67Ghz.  Could do a 4Ghz run if anyone wanted.

---

### Post by Ginsu543 on 2010-01-18
Thanks for letting me know about this app. I'm pleasantly surprised that my aging rig can keep up (sorta) with the i5/i7 systems out there. It's nice to know that it still has some kick left in it. The processor is an Intel Core 2 Duo E6600 overclocked to 3.42 GHz stable, running SST v. 1.1.0 for x86_64. The rest  you can see in my siggy.

Just for comparison, my Dell Mini 9 with Intel Atom N270 @ 1.6 GHz (stock) with 2 GB HyperX DDR2 SODIMM finished the x86 test in 2m 50.305s (sorry, I can't post a screenshot because the 1024 x 600 screen is too small for the SST result window to fit and it won't let me capture a screenshot of the window).

---

### Post by fromthehill on 2010-01-18
> **Ginsu543 said:**
> Thanks for letting me know about this app. I'm pleasantly surprised that my aging rig can keep up (sorta) with the i5/i7 systems out there.not surprising when you overclock your processor to run faster than the fastest core i7 :D
this app uses only one core anyway

acer aspire 8930g - core2duo 2GHz - 3GB ram - 32 bit(found 64bit to be a pain)
borwein - 1M - 1 thread
   0h  0m 58.053s

borwein - 1M - 2 threads
   0h  1m 35.836s

---

### Post by Ginsu543 on 2010-01-18
> **fromthehill said:**
> not surprising when you overclock your processor to run faster than the fastest core i7 :D
this app uses only one core anywayYeah, I wonder what kinds of speeds could be achieved if the program took advantage of every core available. Obviously, two cores can't compete with four, but I'd like to know how much more performance a quad-core can truly bring.

Overclocking can be such a crap shoot, but I was very happy that my components could handle a full 1 GHz overclock over stock. I actually used to run it at 3.6 GHz but the latest BIOS update for my motherboard removed the highest voltage setting. So 3.4 GHz is the highest I can go.

BTW, in your siggy, when you say you went from Win95 > Win90, did you mean Win98?

---

### Post by fromthehill on 2010-01-18
> **Ginsu543 said:**
> Yeah, I wonder what kinds of speeds could be achieved if the program took advantage of every core available. 
ran it with 2 threads
it used the full 2 cores but was painfully slow :D

I'm going to try it on my core i7 940 when I have some spare time 


> BTW, in your siggy, when you say you went from Win95 > Win90, did you mean Win98?
](*,)
fixed:D

---

### Post by Ginsu543 on 2010-01-18
Wow, I am so tempted to and am so far away from being able to afford to build myself a new core i7 rig that I can taste it (well, at least the thought of it)! fromthehill, let's see that awesome system of yours roar! :)

---

### Post by YeOK on 2010-01-18
Not sure I did this right, my results seem wrong some how.

AMD Phenom 2 x4 @ 3.25Ghz. I ran the x86_64 1.1.0 version. (Pre built)
4GB Corsair DDR2 800.
Fedora 12 x86_64. (I don't currently have Ubuntu installed)

---

### Post by futz on 2010-01-18
> **futz said:**
> I meant whether you're using the x86 or 64-bit version. :)
Umm... Never mind. :redface: I see there's a box near the bottom of the program window that says 32 or 64 bit.

---

### Post by futz on 2010-01-18
> **fromthehill said:**
> this app uses only one core anyway
But when you use multiple threads doesn't it use multiple cores? I run a quad core. When I run a 4 thread pass and watch it in System Monitor I can see all four cores go to 100% or near and stay there till SST is done. Still doesn't run as fast as a single thread pass though...

Here's a 4-thread pass with the 64-bit version:
[ATTACH]144043[/ATTACH]

Compare that with a 1-thread pass with 64-bit:
[ATTACH]144048[/ATTACH]


And a 4-thread pass with the 32-bit version:
[ATTACH]144044[/ATTACH]

Compare with a 1-thread pass with 32-bit:
[ATTACH]144046[/ATTACH]

---

### Post by fromthehill on 2010-01-18
> **futz said:**
> But when you use multiple threads doesn't it use multiple cores? I run a quad core. When I run a 4 thread pass and watch it in System Monitor I can see all four cores go to 100% or near and stay there till SST is done. Still doesn't run as fast as a single thread pass though...
what's the use of benchmarking more cores when it runs slower with each core:)

> Wow, I am so tempted to and am so far away from being able to afford to build myself a new core i7 rig that I can taste itwish I had time to use it :P

---

### Post by Psumi on 2010-01-18
> **futz said:**
> I meant whether you're using the x86 or 64-bit version. :)

Should be obvious that I can't use x64 version on my machine.

---

### Post by futz on 2010-01-18
> **Psumi said:**
> Should be obvious that I can't use x64 version on my machine.
Probably, but I didn't look up your CPU to see what exactly it was. I'm unfamiliar with laptop CPUs.

---

### Post by Psumi on 2010-01-18
> **futz said:**
> Probably, but I didn't look up your CPU to see what exactly it was. I'm unfamiliar with laptop CPUs.

Should be common sense now that the ubuntu community requires a large common sense from any of its users.

---

### Post by NoaHall on 2010-01-18
On my second computer - my main is busy compiling something right now. I'll run it on my main later, which has a higher overclock, and much more ram.

---

### Post by YeOK on 2010-01-18
> **NoaHall said:**
> On my second computer - my main is busy compiling something right now. I'll run it on my main later, which has a higher overclock, and much more ram.

Nice, so my results seem correct. Looks like AMD did something well after all.

---

### Post by ryanrich on 2010-03-15
Nice one guys, was looking for something to test my system on 9.10 while adjusting my overlooking settings! Pretty chuffed with my old CPU actually...

---

### Post by cj.surrusco on 2010-05-13
Just built this computer last week, haven't even got the memory to run at full speed yet, it's still running at 533mhz... so I think 11.8s isn't too bad. Also, I got 3m 11s on 8M. My computer froze up halfway trying to do a 16M... maybe I should bring it back down to stock clock before trying that again. Running 10.04 amd64, by the way.

---

### Post by Warpnow on 2010-05-14
Core 2 Duo e6750, 1 thread, Borwein:
```

 -----------------------------------------
 Turn:   1  Errors:   0       Threads:   1
 Running For:  0h  0m  0.000s  ChkErr:   0
 Failed After:  No fail yet
 -----------------------------------------
 Loop Digits State    Time
 ---------------------------------
    0      2  N/A   0h  0m  2.513s
    1      4  N/A   0h  0m  4.737s
    2      8  N/A   0h  0m  6.949s
    3     16  N/A   0h  0m  9.167s
    4     32  N/A   0h  0m 11.374s
    5     64  N/A   0h  0m 13.603s
    6    128  N/A   0h  0m 15.839s
    7    256  N/A   0h  0m 18.052s
    8    512  N/A   0h  0m 20.260s
    9     1K  N/A   0h  0m 22.472s
   10     2K  N/A   0h  0m 24.680s
   11     4K  N/A   0h  0m 26.886s
   12     8K  N/A   0h  0m 29.089s
   13    16K  N/A   0h  0m 31.302s
   14    32K  N/A   0h  0m 33.520s
   15    64K  N/A   0h  0m 35.735s
   16   128K  N/A   0h  0m 37.954s
   17   256K  N/A   0h  0m 40.183s
   18   512K  N/A   0h  0m 42.421s
   19     1M  N/A   0h  0m 43.316s
 Checksum validation...Borwein PASSED!!!

```

---

### Post by cj.surrusco on 2010-05-15
It seems like AMD CPU's are outperforming comparable Intel CPU's. I'm very surprised. Intel is usually considered to be better.

---

### Post by happyhamster on 2010-05-15
> **cj.surrusco said:**
> It seems like AMD CPU's are outperforming comparable Intel CPU's. I'm very surprised. Intel is usually considered to be better.
I think it's the same problem as with most benchmarking utilities, but in reverse. To get a good idea of the power of a cpu, you have to use a benchmarking program that can utilize that cpu to the fullest extent. But most programs are compiled on and optimized for one platform only (and some are partly written in optimized machine-language, which makes it even harder to get a meaningful comparison). In other words: a lot of benchmarking utilities are optimized for Intel, but not in this case.

To test this, compile the program yourself (you'll need the packages build-essential, libqt4-dev and libgmp3-dev, and perhaps more). The resulting binary should be more optimized for your architecture. In my case, Intel P8400 @ 2266Mhz, 64 bits, the time to complete a run decreased from 35 to 18 seconds.

On, an AMD system (Athlon II x2 250 @ 3013Mhz, 64 bits) both pre-compiled and self-compiled binary gave the same result of 14.5 seconds.

Note that there still seems to be something off with the reported cpu frequencies: this is solved by running systester-cli as root. There's no need to do this though, because it doesn't appear to decrease the time running the self-compiled binary. And running an untrusted application as root is a BAD idea anyway.

So, in short: for Intel systems, you'll likely have to compile systester manually.

---

### Post by Lem on 2010-05-19
Overclocked Q9300 - 13.474s

---

### Post by cj.surrusco on 2010-05-19
> **Lem said:**
> Overclocked Q9300 - 13.474s

Did you use the pre-compiled version?

---

### Post by Warpnow on 2010-05-20
Holy ****. I compiled it myself and it went down to 30 seconds. Down a whole 13 seconds...

---

### Post by cj.surrusco on 2010-05-20
My SuperPi 1M time in Windows is over 20s but it is about 11s with SST with the same exact setup... But that may have to do with the architechture, my Windows installation is 32bit. Or possibly SuperPi is made with Intel Cpu's in mind.

---

