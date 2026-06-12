---
title: "128-bit AMD Phenom processor"
date: 2007-11-19
forum: The Cafe
---

### Post by jpittack on 2007-11-19
Could you tell me if this means that the processor is now capable of 128-bit architecture?

[http://www.tomshardware.com/2007/11/19/the_spider_weaves_its_web/page3.html]("http://www.tomshardware.com/2007/11/19/the_spider_weaves_its_web/page3.html")

> The Phenom's SSE unit is being widened to 128 bits , up from the Athlon 64's 64 bit unit.

Its not all that important, as only half of Linux users and mabye 5 % of Windows users decide to use 64 bit. ( Could someone tell me what Mac's OS is)

Still, I've always liked used 64-bit, even thought I don't have any performance gains for the applications I use.

When would Ubuntu consider starting to use 128-bit architecture for the OS?  Would it be a few years after the processors comes out, or would a developmental OS be started within a few months?

---

### Post by LowSky on 2007-11-19
64bit was developed so that a system could use more than 4Gb of RAM
64bit is  capable of using a few million terrabytes of RAM 

So using 128 bit wont be needed for a long time, while most systems will be needing a 64 bit processor within a few years.

---

### Post by jpittack on 2007-11-19
I have heard of performance boosts from using the 64 bit architecture.  And I really hope that one day I will not need a terabyte of RAM.  If I do, I hope I wave my hand and the task is done.

---

### Post by mivo on 2007-11-19
> **jpittack said:**
> Its not all that important, as only half of Linux users and mabye 5 % of Windows users decide to use 64 bit.

That'll change once Microsoft decides to pay attention to 64-bit processors, if only to use it for marketing purposes. Currently, 64-bit Windows seems to be horrible, by what I read, so there is little motivation for MS to promote it.

I use 64-bit versions of Linux, and there are no problems, except needing a 32-bit browser for full Java support. But that will eventually change when Sun releases a 64-bit version of the plugins and Javaws.

---

### Post by jpittack on 2007-11-19
I did try 64 bit Windows and had little trouble with it, but as stated before, I don't use many applications that really take an advantage of it.

---

### Post by mivo on 2007-11-19
Same here (well, in Linux), except some video decoding -- but whether the five files I decode a week take two minutes or ninety seconds makes no difference. ;) Then again, since I have 64-bit hardware, I would never use anything else on it, especially since in time most everyone will use a 64-bit box, so more apps that were designed from scratch for 64-bit will show up.

---

### Post by Lostincyberspace on 2007-11-19
> **LowSky said:**
> So using 128 bit wont be needed for a long time, while most systems will be needing a 64 bit processor within a few years.

Dont say that it wasn't that long ago that we used a 16 bit and it has only been about ten years since so who knows what will happen in the future. I know people who would love to have a terabyte plus of memory. :)


EDIT:never mind I just found out that 64 bit goes al the way upto 16 exabytes or terabyte*1024*1024

---

### Post by ssam on 2007-11-19
is it a SIMD (Single Instruction, Multiple Data) thing like altivec?

there have been a few 128bit CPUs [http://en.wikipedia.org/wiki/128-bit](http://en.wikipedia.org/wiki/128-bit)

128 bit is good for high precision simulation.

---

### Post by happysmileman on 2007-11-19
The SSE unit moving to 128-bit doesn't necessary mean the processor is 128-bit. It would require 128-bit registers and memory adresses at least. AFAIK

---

### Post by mips on 2007-11-19
> **jpittack said:**
> Could you tell me if this means that the processor is now capable of 128-bit architecture?


No, it's not a 128bit CPU, just 64bits. The 128bit only refers to the SSE registers.

---

### Post by Lostincyberspace on 2007-11-19
the total size for RAM of a maxed out  128 bit computer would be 288230376151711744 Yobibytes. Thats enough to hold all the words ever spoken by all people.

---

### Post by Mazza558 on 2007-11-19
> **Lostincyberspace said:**
> the total size for RAM of a maxed out  128 bit computer would be 288230376151711744 Yobibytes. Thats enough to hold all the words ever spoken by all people.

Might come in handy some day. 

Heck, 1 Terabyte ought to be enough for anybody...

(I'm going to regret saying that in 20 years, heh)

---

### Post by Lostincyberspace on 2007-11-19
correction the above should read 288230376151711744 zebibytes or 281474976710656 yobibytes. I would go further with the prefixes but their are none yet.

---

### Post by Lostincyberspace on 2007-11-19
You would need 5 more powers to use it easily. 256*1024^12

---

### Post by jpittack on 2007-11-19
After reading more of the article, I found that the processors from AMD that cost half as much do better on the benchmarks and dual core applications ( not much of a suprise).  I was wondering if Ubuntu is optimized for a certain number of cores, or if any applications are, and how I can find out.

---

### Post by Lostincyberspace on 2007-11-19
most programs right now are optimized for 1 core within the next couple of years that will change.

---

### Post by p_quarles on 2007-11-19
> **Lostincyberspace said:**
> the total size for RAM of a maxed out  128 bit computer would be 288230376151711744 Yobibytes. Thats enough to hold all the words ever spoken by all people.
and almost enough to run Vista!

---

### Post by w7kmc on 2007-11-19
Even though Microsoft has paid scant attention to the 64Bit processor...it seems their operating system needs are  rapidly approaching the 4 GB threshold just to be able to run. Vista takes, what 2 or 3 GB to run cleanly now?

It seems odd the Linux concentrates more heavily on 64 Bits when it is such a lighter operating system.

---

### Post by p_quarles on 2007-11-19
> **w7kmc said:**
> Even though Microsoft has paid scant attention to the 64Bit processor...it seems their operating system needs are  rapidly approaching the 4 GB threshold just to be able to run. Vista takes, what 2 or 3 GB to run cleanly now?

It seems odd the Linux concentrates more heavily on 64 Bits when it is such a lighter operating system.
Nah, it runs fine on 1 GB. It *is *bloated, though, which means XP on 1 GB is a much nicer experience.

---

### Post by -grubby on 2007-11-19
> **Mazza558 said:**
> Might come in handy some day. 

Heck, 1 Terabyte ought to be enough for anybody...

(I'm going to regret saying that in 20 years, heh)

are you using 640K of RAM right now?

---

### Post by LaRoza on 2007-11-19
> **w7kmc said:**
> 
It seems odd the Linux concentrates more heavily on 64 Bits when it is such a lighter operating system.

64 bit seems to be easily used by Linux, whereas, Windows has a 64 bit version, but has no apps. You would think MS would make a 64 bit MS Office Suite if only for the extra money they could make. Think of the marketing!

The Linux ways makes Linux as heavy or as light as one wants. In contrast to some other distros, Ubuntu is quite heavy, and to others, it is light. Either way, you can do a minimal install and add only the packages you want, or you can use another distro.

---

### Post by kopinux on 2007-11-19
like what is said, linux will be everywhere. we cant stop it.

---

### Post by jpittack on 2007-11-19
If you don't use Aero in Vista, 1 gb is enough, but can still have some issues that would be resolved with mabye an extra 256 mb.  In Ultimate, idle can be 1.05 gb.  I see vista as a take care of the users failures to act.  Windows defender updates and runs by itself.  Same with windows update.  All you need to do is give it permission.

I have really enjoyed using linux because I can use 64 bit.  Now I just need to get a tickless kernel.

---

### Post by Lostincyberspace on 2007-11-19
> **p_quarles said:**
> and almost enough to run Vista!

Only if you run it on a cluster. :lol:

---

### Post by Tuna-Fish on 2007-11-19
The reason linux developement is mainly in 64 bits now is that servers generally already have 4GB or more, and most of linux developement is for them.

---

### Post by jpkotta on 2007-11-20
OK, someone already pointed this out, but I will too, because it seems like a lot of people here don't get it.  SSE refers to a specific set of instructions mainly used for number crunching (e.g. video encoding).  The fact that they are 128-bit means about as much as 80-bit floating point registers.  It has nothing to do with addressing, and everything to do with numerical precision.

---

### Post by jpittack on 2007-11-20
I know nothing of how a processer works.  Even worse, I know nothing of bits, as is evident in my posts in the programming section of the forum.  Could you explain 80 bit floating point registers and what is meant by addressing.

---

### Post by kuja on 2007-11-20
> **jpittack said:**
> ( Could someone tell me what Mac's OS is)

"Mac OS X v10.5 supports 64-bit GUI applications using Cocoa, Quartz, OpenGL and X11 on 64-bit Intel-based machines, as well as on 64-bit PowerPC machines.[7] All non-GUI libraries and frameworks also support 64-bit applications on those platforms.

Mac OS X v10.4.7 and higher versions of Mac OS X v10.4 support 64-bit command-line tools using the POSIX and math libraries when run on 64-bit Intel-based machines, just as all versions of Mac OS X v10.4 and higher support them on 64-bit PowerPC machines. No other libraries or frameworks support 64-bit applications in Mac OS X v10.4.[8]"

[http://en.wikipedia.org/wiki/X86-64#Mac_OS_X](http://en.wikipedia.org/wiki/X86-64#Mac_OS_X)

---

### Post by JBAlaska on 2007-11-20
Streaming SIMD Extension 5 (SSE5) is a new extension to the AMD64 (x86=64) instruction set. SSE5 adds 170 new instructions and will be available starting with the Bulldozer processor core due to be released in 2009. These instructions will have greater benefits in domains like HPC, multimedia, and security applications than previously released SSE instruction sets.

SSE5 instructions typically operate on 128-bits of data at a time, as do previously released SSE instruction sets. These new instructions aim to increase work per instruction and remove additional overhead for storing and reloading of register operands through the introduction of an additional operand.
The new instructions include

    * Fused multiply accumulate (FMACxx) instructions
    * Integer multiply accumulate (PMAC, PMADC) instructions
    * Permutation and conditional move instructions
    * Vector compare and test instructions
    * Precision control, rounding, and conversion instructions

Reference PDF: ```
http://www.amd.com/us-en/assets/content_type/white_papers_and_tech_docs/43479.pdf
```

---

### Post by mivo on 2007-11-20
> **Tuna-Fish said:**
> The reason linux developement is mainly in 64 bits now is that servers generally already have 4GB or more, and most of linux developement is for them.

The irony is that my desktop has 3 GB, and even in KDE with just about everything I use daily running, Linux still never uses more than 1 GB! Right now, I have running: KOffice, two Konqueror instances (files,  web), Kopete, Kontact (KMail), KTorrent, four terminal instances, Kaffeine (playing a movie), Basket, Compiz-Fusion with many effects enabled, four workspaces, KSysGuard ... and of my 3 GB RAM, about 800 MB are used by applications (most of the rest is for disk caching, but that doesn't count since it is readily available to the apps if needed). I wonder how much RAM would be available if I did the same in Vista with similar applications.

---

### Post by hardyn on 2007-11-20
> **jpittack said:**
> After reading more of the article, I found that the processors from AMD that cost half as much do better on the benchmarks and dual core applications ( not much of a suprise).  I was wondering if Ubuntu is optimized for a certain number of cores, or if any applications are, and how I can find out.

That used to be case with the althon/p4s but not the case anymore; C2D delivered a bit of a crushing blow to AMD

---

### Post by hardyn on 2007-11-20
> **jpittack said:**
> I know nothing of how a processer works.  Even worse, I know nothing of bits, as is evident in my posts in the programming section of the forum.  Could you explain 80 bit floating point registers and what is meant by addressing.

well addressing, all components have a specific memory address, and how the programmer or compiler makes sure that the right data goes to the right place, an analog would be a postal system.

(quick dirty analogy, no flames please)
for example 'hello world' might be stored in a range of memory from x-y were each letter could be extracted from an address between the range x.0 might have 'h' x.1 might hold 'e'; but not always contiguously.  likewise system components like the video card have memory addresses as well, that can be accessed by the programmer or the compiler.

80bit is the size of the mailbox... how much data can be stored, accessed or manipulated at a given time.

registers are VERY high speed memory located on the processor core its self usually only a handful are available for the processor, and are used to store the data that is to be/has been processed, data does not usually stay in the register for very long, and is moved in to one of the caches, ram or disk shortly after

wikipedia does a good job with technical stuff like this.

---

### Post by stinger30au on 2007-11-20
> **p_quarles said:**
> and almost enough to run Vista!

:lolflag::lolflag::lolflag:

yep, sounds about right

---

