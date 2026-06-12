---
title: "cisc vs. risc and 64 bit"
date: 2010-09-09
forum: The Cafe
---

### Post by chris200x9 on 2010-09-09
I am just wondering did the computer industry miss a huge opportunity? Since we've pretty much moved away from 32 bit in general could chip makers have made a 64 bit chip that could had one 32 bit core that would run x86 for legacy operating system purposes, but then 3 cores (assuming quad core) 64 bit but with a new next generation instruction set. We would have to port everything to 64 bit anyway (much like we are doing today). After enough had migrated to the new 64 bit, manufacturers could ship pure 64 bit cpus. After this for the next couple of generations of operating systems could have have a cpu emulator for x86 built in. After time it would be like qemu where it is a seperated download.

---

### Post by del_diablo on 2010-09-09
Besides ARM(36 bit was it?), what instruction sets is still 32-bits these days?

---

### Post by juancarlospaco on 2010-09-09
No 32bit behind year 2038.

---

### Post by chris200x9 on 2010-09-09
> **del_diablo said:**
> Besides ARM(36 bit was it?), what instruction sets is still 32-bits these days?

I think you missed my point I'm asking since we moved to 64 bit and everything had to be ported anyway did we miss an opportunity to introduce a new better intruction set than x86.

---

### Post by toupeiro on 2010-09-09
> **chris200x9 said:**
> I think you missed my point I'm asking since we moved to 64 bit and everything had to be ported anyway did we miss an opportunity to introduce a new better intruction set than x86.

There are already better architectures out there than x86, and have been for a while.  However, there are none as commodity, or widely adopted.  If the Intel's and AMD's of the world were to change gears, it would be a HUGE disturbance of the force in the software development and Operating system world.  Mac was able to go from PPC to x86 with more ease in their transition because of their tightly closed approach at software and architecture (that and a much smaller hardware marketshare overall compared to x86 systems)

MIPS and SPARC are both superior architectures (purely RISC instruction sets) in my mind to x86, but there is a higher price point associated with them, and most people really don't need that kind of compute power.  x86 has truthfully been somewhat of a hybrid risc/cisc architecture anyways for many years.  (RISC CPU on a CISC interface).  You have to back to like 1st and 2nd generation Pentium processors to get to a purely CISC based instruction set.  I believe I read somewhere that the Pentium Pro was the first Hybrid.

---

### Post by Bachstelze on 2010-09-09
> **chris200x9 said:**
> Since we've pretty much moved away from 32 bit in general could chip makers have made a 64 bit chip that could had one 32 bit core that would run x86 for legacy operating system purposes, but then 3 cores (assuming quad core) 64 bit but with a new next generation instruction set.

No.

That is, not unless Microsoft is willing to release a new version of its "legacy" OSes with support for such hybrid CPUs.

---

### Post by del_diablo on 2010-09-11
> **toupeiro said:**
> Mac was able to go from PPC to x86 with more ease in their transition because of their tightly closed approach at software and architecture (that and a much smaller hardware marketshare overall compared to x86 systems)

They got Dawnina or something as the Kernel, lots of cross compatible FOSS stuff under the hood, all they had to port was the main api.
Reminds me: Rosetta was their emulation layer called?

MIPS and SPARC are both superior architectures (purely RISC instruction sets) in my mind to x86, but there is a higher price point associated with them, and most people really don't need that kind of compute power.  x86 has truthfully been somewhat of a hybrid risc/cisc architecture anyways for many years.  (RISC CPU on a CISC interface).  You have to back to like 1st and 2nd generation Pentium processors to get to a purely CISC based instruction set.  I believe I read somewhere that the Pentium Pro was the first Hybrid.[/QUOTE]

x86 is CISC, but running it over RISC gave performance increase, so Intel and AMD did what the wise do.
However, in the end the real "problem" is that the "mainstream" of the computer marked is a useless blob that refuses to aknowledge that there exists more option than what the useless stores would provide the fools.
Add on a few ridicules EEE from MS, and we look sadly at todays somewhat reverting situation.
A point: x86 is not cheaper CPU's than other Architectures, it is just that it is mass-produced a lot more of them. And that is again why ARM is interisting: Super to x86 like most instruction sets, but its actually bulk produced enough to start in the price war.

---

### Post by toupeiro on 2010-09-11
> **del_diablo said:**
> They got Dawnina or something as the Kernel, lots of cross compatible FOSS stuff under the hood, all they had to port was the main api.
Reminds me: Rosetta was their emulation layer called?

x86 is CISC, but running it over RISC gave performance increase, so Intel and AMD did what the wise do.
However, in the end the real "problem" is that the "mainstream" of the computer marked is a useless blob that refuses to aknowledge that there exists more option than what the useless stores would provide the fools.
Add on a few ridicules EEE from MS, and we look sadly at todays somewhat reverting situation.
A point: x86 is not cheaper CPU's than other Architectures, it is just that it is mass-produced a lot more of them. And that is again why ARM is interisting: Super to x86 like most instruction sets, but its actually bulk produced enough to start in the price war.

Interesting point.  Do you have any data you can share that outlines the production cost of modern x86 versus modern SPARC or MIPS?  It'd be really interesting to see, considering the noted price difference in platform when you go to buy it.

---

### Post by jerenept on 2010-09-11
> **chris200x9 said:**
> I am just wondering did the computer industry miss a huge opportunity? Since we've pretty much moved away from 32 bit in general could chip makers have made a 64 bit chip that could had one 32 bit core that would run x86 for legacy operating system purposes, but then 3 cores (assuming quad core) 64 bit but with a new next generation instruction set. We would have to port everything to 64 bit anyway (much like we are doing today). After enough had migrated to the new 64 bit, manufacturers could ship pure 64 bit cpus. After this for the next couple of generations of operating systems could have have a cpu emulator for x86 built in. After time it would be like qemu where it is a seperated download.

AMD figured out an easier way: x86-64.

It can run 32-bit code just as fast as 64-bit code.

---

### Post by toupeiro on 2010-09-11
> **jerenept said:**
> AMD figured out an easier way: x86-64.

It can run 32-bit code just as fast as 64-bit code.

That's just the generalized name for 64-bit x86 architecture.  x86_64.  Thats the name of it whether you run Intel or AMD:

Core i7:
```
uname -a
Linux mobius 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux
```

---

### Post by jerenept on 2010-09-11
> **toupeiro said:**
> That's just the generalized name for 64-bit z86 architecture.

I think you mean AMD64 or ia64 for intel

[http://en.wikipedia.org/wiki/X86-64]("http://en.wikipedia.org/wiki/X86-64")

> x86-64 is an extension of the x86 instruction set. It supports vastly larger virtual and physical address spaces than are possible on x86, thereby allowing programmers to conveniently work with much larger data sets. x86-64 also provides 64-bit general purpose registers and numerous other enhancements. The original specification was created by AMD, and has been implemented by AMD, Intel, VIA, and others. It is fully backwards compatible with 32-bit code.[1](p13) Because the full 32-bit instruction set remains implemented in hardware without any intervening emulation, existing 32-bit x86 executables run with no compatibility or performance penalties,[2] although existing applications that are recoded to take advantage of new features of the processor design may see significant performance increases.

---

### Post by toupeiro on 2010-09-11
> **jerenept said:**
> [http://en.wikipedia.org/wiki/X86-64]("http://en.wikipedia.org/wiki/X86-64")

ok.. all I am saying is, it refers to 64-bit x86 architecture.  It's generalized.  This is what EVERYONE did that makes x86 chips, not just amd.

---

### Post by linux18 on 2010-09-11
I think the true meaning of this thread is: ignoring cost and availability, which architecture has the best performance/transistor ratio?

I vote for sparc64

---

### Post by cprofitt on 2010-09-11
> **toupeiro said:**
> There are already better architectures out there than x86, and have been for a while.  However, there are none as commodity, or widely adopted.  If the Intel's and AMD's of the world were to change gears, it would be a HUGE disturbance of the force in the software development and Operating system world.  Mac was able to go from PPC to x86 with more ease in their transition because of their tightly closed approach at software and architecture (that and a much smaller hardware marketshare overall compared to x86 systems)

Oh... and the fact that what OS X was (NeXT) was actually built and compiled in Intel x86 originally.. and from what I understand was always complied and tested in x86 and then recompiled for PPC.

---

### Post by chris200x9 on 2010-09-11
> **Bachstelze said:**
> No.

That is, not unless Microsoft is willing to release a new version of its "legacy" OSes with support for such hybrid CPUs.

they wouldn't need to, "legacy os" boot the 32 bit x86 core the others site idle, recent os boots the 64 bit cores with new instruction set. All this until almost everything is new 64 bit compatible, then running legacy apps moves into the os providing cpu emulation like macs rosetta.At whichh point you could ditch the old 32 bit x86 core.

---

### Post by toupeiro on 2010-09-11
> **cprofitt said:**
> Oh... and the fact that what OS X was (NeXT) was actually built and compiled in Intel x86 originally.. and from what I understand was always complied and tested in x86 and then recompiled for PPC.

Interesting, I didn't know that.  What about the 9 or so versions before OS-X, Where they cross-compiled as well?

---

### Post by Dr. C on 2010-09-11
What is holding back risc on the desktop is Microsoft and propriety Windows applications. For Microsoft risc on the desktop would be an absolute disaster. Sure Microsoft can easily port Windows 7 to risc but they cannot port the whole Windows ecosystem (applications and drivers) to risc, as they have the source code only for the OS but not for the rest. On the other hand the competition for example Canonical can port almost the entire GNU / Linux ecosystem to risc and has already done so.

ARM has being lobbying Microsoft for years to port desktop Windows to risc. Microsoft's response: rename Windows Mobile to Windows ***Phone***. Not only is Microsoft not willing to support risc on the desktop, they will not support risc on tablets or small netbooks! 

Even the move from 32 bit to 64 bit is still problematic (driver support for legacy peripherals) when one sees a notebook with 4GB of ram being sold with a 32bit version of Windows 7 pre installed that only uses 75% or the installed ram. 

For Microsoft to port desktop Windows to risc would be tantamount to laying down in the path of a heard of [stampeding gnus]("http://www.youtube.com/watch?v=tfB18zOswaE") and waiting to be trampled to death.

---

### Post by lloyd_b on 2010-09-11
> **FineE said:**
> 
For Microsoft to port desktop Windows to risc would be tantamount to laying down in the path of a heard of [stampeding gnus]("http://www.youtube.com/watch?v=tfB18zOswaE") and waiting to be trampled to death.
I think you're overstating things just a *bit* :),  but that's not a completely invalid point.  In order for MS to market an OS for any non-X86 platform, they'll need to provide a good X86 emulation layer so that the zillions of legacy programs which are compiled for X86 will continue to work.  To do otherwise would be to severely risk the "lock-in" that they've spent a great deal of time and money establishing.

Lloyd B.

---

### Post by cprofitt on 2010-09-11
> **toupeiro said:**
> Interesting, I didn't know that.  What about the 9 or so versions before OS-X, Where they cross-compiled as well?

I do not think they were, but I am not 100% sure. Especially on the version that were on the Apple II and original Macs... not even sure what processors were used in those.

---

### Post by Dr. C on 2010-09-11
> **lloyd_b said:**
> I think you're overstating things just a *bit* :),  but that's not a completely invalid point.  In order for MS to market an OS for any non-X86 platform, they'll need to provide a good X86 emulation layer so that the zillions of legacy programs which are compiled for X86 will continue to work.  To do otherwise would be to severely risk the "lock-in" that they've spent a great deal of time and money establishing.

Lloyd B.

Of course they would have to provide good x86 emulation to run existing Windows applications but that is far from enough. 

First GNU / Linux would would do the same and get similar or better performance by running the entire legacy Windows OS and applications in an x86 emulator. In addition GNU / Linux would have a huge advantage in hardware and peripheral support because of few drivers available for the risc Windows. Even worse the applications that would be ported en mass to the risc Windows are the very same FLOSS applications that also are available on GNU / Linux. One for example would have GIMP running native competing with Photoshop running in an x86 emulator on Windows! 

The interesting thing is that Microsoft has already been there and done that (including the x86 emulator) back in the mid 1990's with Windows NT on risc. The last version of Windows to support risc was NT4.

---

### Post by jrusso2 on 2010-09-12
> **FineE said:**
> Of course they would have to provide good x86 emulation to run existing Windows applications but that is far from enough. 

First GNU / Linux would would do the same and get similar or better performance by running the entire legacy Windows OS and applications in an x86 emulator. In addition GNU / Linux would have a huge advantage in hardware and peripheral support because of few drivers available for the risc Windows. Even worse the applications that would be ported en mass to the risc Windows are the very same FLOSS applications that also are available on GNU / Linux. One for example would have GIMP running native competing with Photoshop running in an x86 emulator on Windows! 

The interesting thing is that Microsoft has already been there and done that (including the x86 emulator) back in the mid 1990's with Windows NT on risc. The last version of Windows to support risc was NT4.


Not true your forgetting about the Windows versions for Itanium which is a risc  cpu

---

### Post by Dr. C on 2010-09-12
> **jrusso2 said:**
> Not true your forgetting about the Windows versions for Itanium which is a risc  cpu

I stand corrected. The last version of Windows to support risc ***on the desktop*** was NT4. There was also XP 64bit on Itanium for high end workstations in 2002 - 2005. Itanium is a server CPU but even there Microsoft is phasing out support. [http://blogs.technet.com/b/windowsserver/archive/2010/04/02/windows-server-2008-r2-to-phase-out-itanium.aspx]("http://blogs.technet.com/b/windowsserver/archive/2010/04/02/windows-server-2008-r2-to-phase-out-itanium.aspx")

---

### Post by NMFTM on 2010-09-12
> **jerenept said:**
> AMD figured out an easier way: x86-64.

It can run 32-bit code just as fast as 64-bit code.
Really? I thought 32 bit code on an x64 CPU ran in emulation mode and was slower than if it were run on an x86 chip of the same speed.

---

### Post by Shining Arcanine on 2010-09-12
> **NMFTM said:**
> Really? I thought 32 bit code on an x64 CPU ran in emulation mode and was slower than if it were run on an x86 chip of the same speed.

You are thinking about Itanium. It was supposed to replace x86, but since it was not neither a CISC architecture nor a RISC architecture, Intel's plan failed.

---

### Post by Dr. C on 2010-09-12
Actually Modern Intel and AMD x86 processors support instruction sets as far back as the 8088/8086 instruction set. So one could run MS-DOS from a floppy on a Core i7 for example. Quite remarkable after close to 30 years.

---

### Post by CraigPaleo on 2010-09-12
> **toupeiro said:**
> Interesting, I didn't know that.  What about the 9 or so versions before OS-X, Where they cross-compiled as well?

Before the PPC, Apple used Motorola CISC processors. I don't believe they ever had a reason to try to be compatible with Intel until they acquired Next, whose NextStep OS became OS X and was already compatible.  

Copeland was to be Apple's homegrown modern OS but they just couldn't seem to get it out the door in a timely fashion. It's some interesting history. Be inc. came along and ported the BeOS from AT&T's Hobbit processor to the PPC and Apple computers in the hopes that Apple would buy Be. Apple went with Next but I think the real reason was to get Steve Jobs back more than it was the operating systems themselves.

---

### Post by Simian Man on 2010-09-12
x86 may be a CISC architecture, but modern chips that implement that architecture are all RISC.  x86 instructions are decoded into micro-operations which are simpler and are used throughout the rest of the pipeline.  The only things that are hard about x86 are decoding it and compiling for it and these are both solved problems.

It may be unfortunate that we are have an ISA that isn't as elegant as we computer scientists would like, but there is seriously nothing to be gained in practical terms from switching to a RISC ISA like Arm, Mips or Sparc for general-purpose computing.

[EPIC]("http://en.wikipedia.org/wiki/Explicitly_parallel_instruction_computing") ISA's like the Itanium are far more lucrative, because they offer a lot more benefits then a cleaner design, but even that failed.

---

### Post by Dr. C on 2010-09-12
One needs to ask why in areas where there does not exist an x86 propriety software infrastructure such as mobile risc is so dominant? There are many advantages to risc in power consumption vs performance etc.

---

### Post by toupeiro on 2010-09-12
> **linux18 said:**
> I think the true meaning of this thread is: ignoring cost and availability, which architecture has the best performance/transistor ratio?

I vote for sparc64

I would agree with you in the desktop to enterprise scale. However, if you truly jump up into HPC, completely ignoring the costs, it's hard to ignore a SicorTex MIPS CPU..  What it can do in a fraction of the footprint and power draw of its x86 competitors is frightening.


A Sicortex desktop, if you have the money, I have no doubts is the most powerful desktop in the world.  Their servers compete with compute clusters of many servers.  It's probably not fair to call them a"Desktop" or "Server".  Just one of their HPC cabinets can provide up to 8.2 TFlops of compute power and only require around 20Kw to do it.  Sicortex picked up where SGI left off with MIPS architecture and brought it to a whole new level.  I did a small presentation on them a couple of years ago.

[http://sicortex.com/products/deskside_development_system](http://sicortex.com/products/deskside_development_system)

---

### Post by Dr. C on 2010-09-12
> **toupeiro said:**
> I would agree with you in the desktop to enterprise scale. However, if you truly jump up into HPC, completely ignoring the costs, it's hard to ignore a SicorTex MIPS CPU..  What it can do in a fraction of the footprint and power draw of its x86 competitors is frightening.


A Sicortex desktop, if you have the money, I have no doubts is the most powerful desktop in the world.  Their servers compete with compute clusters of many servers.  It's probably not fair to call them a"Desktop" or "Server".  Just one of their HPC cabinets can provide up to 8.2 TFlops of compute power and only require around 20Kw to do it.  Sicortex picked up where SGI left off with MIPS architecture and brought it to a whole new level.  I did a small presentation on them a couple of years ago.

[http://sicortex.com/products/deskside_development_system](http://sicortex.com/products/deskside_development_system)

Actually when one considers the processing power this system is extremely economical. We are taking a 72 core system with 48GB of memory for $23,695.00. Furthermore it consumes only about 300 watts of electricity.

---

### Post by toupeiro on 2010-09-13
> **FineE said:**
> Actually when one considers the processing power this system is extremely economical. We are taking a 72 core system with 48GB of memory for $23,695.00. Furthermore it consumes only about 300 watts of electricity.

I hear ya.  23K desktops is typically out of scope for most.  And, while this system comes with RHEL5, It takes a lot of compiling and porting of various libraries to support it.  I can build a dual-hex core Xeon system with 48GB of RAM (after hyperthreading, 24 cores total) about 55% cheaper than this SiCortex system, but it won't out-compute it by any shot, and it will probably suck up as much, if not more electricity.  If you have the source code for your apps and libraries, and you need HPC power, it is a very attractive item that shouldn't be overlooked.

---

### Post by bertolo on 2011-01-06
why bother to add a 32 bit processor in a quadcore when u can have the same instructions from 32bit in 64bit tecnology

u can emulate fully a 32bit processor in a 64 bit one, at least i think so

---

### Post by mips on 2011-01-06
Technically we are all running RISC processors with an CISC x86 decoding front-end since AMD K5 days.

Modern RISC CPUs have much larger instructions sets and they are all beginning to look like each other.

---

