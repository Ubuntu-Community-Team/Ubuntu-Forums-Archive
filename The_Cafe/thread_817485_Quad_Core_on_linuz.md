---
title: "Quad Core on linuz"
date: 2008-06-03
forum: The Cafe
---

### Post by Raccoon1400 on 2008-06-03
A friend of mine said vista was the only OS that knew how to handle a quad core properly. I am almost certain this is wrong. Can anyone back me up?

---

### Post by Perfect Storm on 2008-06-03
The 2.6 kernel supports SMP and this should be taking are of multi-processor systems. So it shouldn't be a problem.

---

### Post by roaldz on 2008-06-03
> **Raccoon1400 said:**
> A friend of mine said vista was the only OS that knew how to handle a quad core properly. I am almost certain this is wrong. Can anyone back me up?

Tell him to gain some computer knowledge. He´s wrong. Linux and Unix in general are your quad-core´s friends:)

---

### Post by 50words on 2008-06-03
I am running Hardy on a quad-core Gateway and it blazes. I have no objective way to tell whether it is using the processor cores "properly," however.

---

### Post by FuturePilot on 2008-06-03
I'm almost positive Linux can handle a quad proccessor. Therefore I say he's wrong.

---

### Post by gameryoshi600 on 2008-06-03
Tell him that vista will ruin your quad core machine

---

### Post by klange on 2008-06-03
Maybe the kernel just decided four cores wasn't a good number. Try getting a few more, say, 100 or so? Should work fine.

---

### Post by bobblehat on 2008-06-03
I've had Ubuntu and Fedora on several quad cores and both run fine. A collegue also asked me to put it on his 2xquad Skulltrail machine (total of 8 xeon cores) and that's fine too.

Running some CPU-intensive testing recently and just looking visually at the system monitor, Ubuntu seems to do a good job of balancing load over the four cores (i.e. all get used roughly equally).

---

### Post by Raccoon1400 on 2008-06-03
Thanks. Now I can back it up when I tell him he is wrong.

bobblehat, I want that octuple core!

---

### Post by gameryoshi600 on 2008-06-03
> **Raccoon1400 said:**
> Thanks. Now I can back it up when I tell him he is wrong.

bobblehat, I want that octuple core!

Your very welcome. and I meant by vista ruins your quad core is that it uses alot of processing so it really wouldn't be worth it with vista. :lolflag:

---

### Post by tamoneya on 2008-06-03
take a look at my sig.  Q6600 works like a charm.  Also take a look near the end of this thread to see some numbers on linux quad cores: 
[http://ubuntuforums.org/showthread.php?t=60264](http://ubuntuforums.org/showthread.php?t=60264)

---

### Post by liquidfunk on 2008-06-03
Think of the PS3 with Yellow Dog Linux the PS3 has an 8-Core PowerPC Cell in it. Albeit only 7 are active, that runs like a charm.

---

### Post by shadylookin on 2008-06-03
I believe linux can run on several hundred if not thousands of processors. please correct me if i'm wrong on this.

---

### Post by Steveway on 2008-06-03
Guess what Operating Systems the best Supercomputers in the world run? Linux? Yup they do!
And they have much more than those pitiful 8 cores.

---

### Post by liquidfunk on 2008-06-03
If you don't believe that, have a look at the Cray supercomputers!

---

### Post by Raccoon1400 on 2008-06-03
> **liquidfunk said:**
> If you don't believe that, have a look at the Cray supercomputers!
I believed it from the start, I wanted support before I tell him he is wrong.

---

### Post by wootah on 2008-06-03
> **Raccoon1400 said:**
> I believed it from the start, I wanted support before I tell him he is wrong.
:popcorn:

---

### Post by drumsticks on 2008-06-03
I recall reading somewhere (sorry, no reference) that Linux is the only kernel capable of distinguishing between HyperThreads and a true dual core/cpu, and therefore schedule accordingly. Is that true?

---

### Post by Raccoon1400 on 2008-06-03
> **drumsticks said:**
> I recall reading somewhere (sorry, no reference) that Linux is the only kernel capable of distinguishing between HyperThreads and a true dual core/cpu, and therefore schedule accordingly. Is that true?
What exactly is hyperthreading, anyways?

I have heard the term, but never a clear definition.

---

### Post by cookieofdoom on 2008-06-03
XP handles a quad core, too, I believe. If XP does, that means that 2000 probably does. In any case, Vista cannot properly handle anything. It has a very annoying tendency to drop things.

---

### Post by tamoneya on 2008-06-03
ive got to think that your friend is referring to the 4 GB barrier that exists between 64 bit and 32 bit operating systems.  It may also be that he knows that quad corse are 64 bit and he thinks he needs 64 bit vista to run them.  any new processor nowadays (dual or quad) is a 64 bit processor and they run on both 32 and 64 bit OSes,

---

### Post by Raccoon1400 on 2008-06-03
My processor is a dual core, and I run 64bit arch. Most of thetime, the CPUs are scaled down to 50% (800MHz)

---

### Post by Dropbear on 2008-06-03
> **50words said:**
> I am running Hardy on a quad-core Gateway and it blazes. I have no objective way to tell whether it is using the processor cores "properly," however.

Type this in a terminal

```
cat /proc/cpuinfo
```

It will tell you at what speed each core is operating at.

---

### Post by Novega on 2008-06-03
> **Dropbear said:**
> Type this in a terminal

```
cat /proc/cpuinfo
```

It will tell you at what speed each core is operating at.

Sorry, not trying to hijack the thread but if my cpu is operating at 1000MHz and it should be at 2.3GHz...how do I fix it? or should I not worry about it? (Desktop system)
I suspect the slowdown is due to power management settings, but I don't know how to fix them?
```
power management: ts fid vid ttp tm stc
```


On topic: the OP's friend is not alone in their assumption, I've been in some VERY heated arguements over the ability of an OS to handle multiple core processors.

---

### Post by saulgoode on 2008-06-04
> **Raccoon1400 said:**
> A friend of mine said vista was the only OS that knew how to handle a quad core properly. I am almost certain this is wrong. Can anyone back me up?

I have never seen any comparisons made between Vista multi-core handling and Linux's. It is my understanding (quite limited, at that) that Linux scheduling across multiple processors used to not scale very well to quad-core and beyond. However, this was about a year ago during the 2.6.20-22 kernels (and it's not as though they failed completely, just that there was room for improvement).

However, the kernel developers have been quite diligently addressing the problem (the Completely Fair Scheduler was initially introduced into 2.6.23) and the developers seem very pleased with the progress made in the 2.6.24 and 2.6.25 kernels in processor efficiency in all configurations (not just quad- and octo-cores).

So it is possible your friend is actually quite knowledgeable on the topic, but that his information is outdated. It would be interesting to know further details about his assessment (assuming it is something more than Microsoft ad copy).

---

### Post by Dropbear on 2008-06-04
> **Novega said:**
> Sorry, not trying to hijack the thread but if my cpu is operating at 1000MHz and it should be at 2.3GHz...how do I fix it? or should I not worry about it? (Desktop system)
I suspect the slowdown is due to power management settings, but I don't know how to fix them?
```
power management: ts fid vid ttp tm stc
```


On topic: the OP's friend is not alone in their assumption, I've been in some VERY heated arguements over the ability of an OS to handle multiple core processors.

Are you running an AMD processor with cool'n quiet enabled? I had that problem. Disabling cool 'n quiet fixed it.

---

### Post by Dropbear on 2008-06-04
I found this article [http://www.phoronix.com/scan.php?page=article&item=897&num=1](http://www.phoronix.com/scan.php?page=article&item=897&num=1) . Although they are testing the ATI drivers the fact they are using a quad core shows linux performing well against vista.

---

### Post by insane_alien on 2008-06-04
linux is used on machines with thousands of cores(supercomputers) i'm pretty sure it can handle 4 easily enough.

also, what about OSX that has very good multicore support as well(seeing as its roots are in unix this should be obvious too)

---

### Post by mini_g on 2008-06-04
> **Raccoon1400 said:**
> What exactly is hyperthreading, anyways?

I have heard the term, but never a clear definition.

[This might be of help.]("http://en.wikipedia.org/wiki/Hyperthreading")

---

### Post by drumsticks on 2008-06-04
> **mini_g said:**
> [This might be of help.]("http://en.wikipedia.org/wiki/Hyperthreading")

Haha.. I was right!*Linux does treat HT*differently (and better!) and more efficiently. Windows just gets fooled ;)

---

### Post by sweeneytodd on 2008-06-04
i feel like homer with his donuts when u say 2*quad, say it again!!!

---

### Post by -random on 2008-06-04
Only prob with the dual/quad's i'm experiencing is when I run a multi-threaded app on wine, it only uses maximum one thread in linux :(

but this is a wine related thang... ubuntu is awesome <3

---

### Post by Golem XIV on 2008-06-04
For a long time Microsoft policy has been that the "home" operating systems do not support multiple processors.  This hasn't changed.

9x, ME, XP Home and Vista Home only support one physical processor (which can have several cores, not sure what is the limit)

Vista Business can support 2 processors.

More than that, you need a Microsoft server OS (2000 server, 2003 server, 2008 server)

Linux does not have this limitation.

---

### Post by 50words on 2008-06-04
> **Dropbear said:**
> Type this in a terminal

```
cat /proc/cpuinfo
```

It will tell you at what speed each core is operating at.

Hmmm. All are running at 1.6 GHz. Which is great and all, but they are all 2.4 GHz processor cores.

---

### Post by Golem XIV on 2008-06-04
> **50words said:**
> Hmmm. All are running at 1.6 GHz. Which is great and all, but they are all 2.4 GHz processor cores.

The CPU is throttled down to keep power consumption and heat down.  If a process requires additional CPU cycles, it will boost it up to full rated frequency.  If you want the CPU to run at full blast all the time, spark up gconf-editor and

Go to apps -> gnome-power-manager -> cpufreq
Change the policy under policy_ac to performance

You will probably need to log off and back on for the settings to take.

---

### Post by Moustacha on 2008-06-04
No idea why you would want it at full-bore all the time, especially when idle. It'll just go threw power and spew out heat.

The current cpu limit on the kernel is around 16K cores I believe, for your desktop needs

---

### Post by ssam on 2008-06-04
4, 8 and 16 core linux severs are pretty common.
[https://secure.dnuk.com/systems/r440hs-2u.php](https://secure.dnuk.com/systems/r440hs-2u.php)

[http://www-03.ibm.com/systems/uk/p/hardware/midrange_highend/index.html](http://www-03.ibm.com/systems/uk/p/hardware/midrange_highend/index.html)
IBM linux servers with 2-64 CPU cores.

[http://www.sgi.com/products/servers/altix/4000/](http://www.sgi.com/products/servers/altix/4000/)
"It supports up to 512 sockets or 1024 cores under one instance of Linux and as much as 128TB of globally shared memory"

in terms of big supercomputers, they mostly run linux and have 1000s of CPUs. though they may act more like a cluster of computers than a single computer.
[http://www.top500.org/stats/list/30/os](http://www.top500.org/stats/list/30/os)

linux can even do CPU hotpluging. that is adding or removing CPUs from a running machine (you need hardware support for this) [http://www.kernel.org/doc/Documentation/cpu-hotplug.txt](http://www.kernel.org/doc/Documentation/cpu-hotplug.txt)

your friend fails :-)

---

### Post by Steveway on 2008-06-05
Also to those that wonde why that command shows less MHZ than they think they have.
Do you have a AMD CPU? If yes then that is perfectly normal.
CPUs from AMD run with less MHZ but are equal to higher clocked Intel-proccessors.
My processor for example is an AMD Sempron 3000+, that means that it has the speed equal to or faster than  a Intel Pentium 4 with 3000 MHZ even though cat /proc/cpuinfo reports "only" 1800 MHZ for that CPU.
Based on my processor I would assume that 50words 1,6 GHZ (respectively 2,4 GHZ) are prefectly normal.
I was surprised seeing people removing powersaving-support on their computers, don't you know how hot those things become under full power? They easily reach 80 or 100 °C! I work in the IT-field and most ICs there brake if they reach more than 68°C.
I prefer my CPU to run at the lowest mode it can (800MHZ real, about 1 or 1,1 GHZ theoretically).

---

### Post by 50words on 2008-06-05
Mine is an Intel, actually, so I am guessing it is just power saving, and it boosts the speed when it needs it. Which is probably never does, since this is my office computer, which I use for e-mail, blogging, and editing documents. Nothing fancy.

---

### Post by jjamulla on 2008-06-07
> **roaldz said:**
> Tell him to gain some computer knowledge. He´s wrong. Linux and Unix in general are your quad-core´s friends:)

Well - Sof ar Ubuntu for me has no clue how to properly set up my Q9300 CPUs, this stupid cpufreq limiting stuff sucks, I just want to turn it off and can't figure out how, did all kinds of stuff so far and it's always running my CPUs at 2 GHz instead of the 2.5.
I also want to overclock this machine, but it can't even get it running at "normal" speed it'd be a waste.

Anyone have a CLUE ( I did ALOT of searches so far) about how to turn off this rediculous cpu limiting stuff, or increase the speed to what it's supposed to be? In dmesg it realizes the CPUs are 2.5 GHz, but /proc/cpuinfo doesn't show more then 2 GHZ or 2.33 (if I fool with the cpufreq stuff)

---

### Post by Brian96 on 2008-06-07
> **jjamulla said:**
> Well - Sof ar Ubuntu for me has no clue how to properly set up my Q9300 CPUs, this stupid cpufreq limiting stuff sucks, I just want to turn it off and can't figure out how, did all kinds of stuff so far and it's always running my CPUs at 2 GHz instead of the 2.5.
I also want to overclock this machine, but it can't even get it running at "normal" speed it'd be a waste.

Anyone have a CLUE ( I did ALOT of searches so far) about how to turn off this rediculous cpu limiting stuff, or increase the speed to what it's supposed to be? In dmesg it realizes the CPUs are 2.5 GHz, but /proc/cpuinfo doesn't show more then 2 GHZ or 2.33 (if I fool with the cpufreq stuff)

I have had some concerns about this as well (and have a thread open about it in the 64 users forum). Honestly, though, I don't know enough about clock cycles to know what it means.

My dilemma with my C2Q Q6600, on which I did the "BSEL tape mod" (which is supposed to boost it from 2.4 to 3.0, and according to CPU-Z it does in Vista). Ubuntu, however, only shows it as 2.4 max, and has it scaled down to 1600 most of the time.

The guy who responded to my other thread said that it is a detection problem, and according to my "bogomips" in cat /proc/cpuinfo, that may be true.

My problem is that I can't "see" it. In Vista, CPU-Z SHOWS me that it is scaling between 1995 and 2995 MHz as demands change. Conky has me at 1600 all the time (or 2400 if I change to "performance") and I never SEE it scaling up to 2400 (much less to the 2995 that I believe I *should* be running at). (EDIT: Actually, as I look again, it does scale up to 2400 from time to time in Conky when running BOINC.) Speaking of BOINC, can anyone help me interpret BOINC's CPU benchmarks?

Even when running stuff with BOINC I don't see any scaling up.

Is there an application for Ubuntu that will give me more accurate processor info?

Oh, and to un-hijack a little, I'm sure Linux does everything better than Vista.

---

