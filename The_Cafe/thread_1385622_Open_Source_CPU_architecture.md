---
title: "Open Source CPU architecture"
date: 2010-01-19
forum: The Cafe
---

### Post by k64 on 2010-01-19
[http://en.wikipedia.org/wiki/Open_source_hardware](http://en.wikipedia.org/wiki/Open_source_hardware)

Sounds pretty ambitious. My question: Will someone be willing to create a whole new CPU architecture that's open source? I'd certainly be pleased.

---

### Post by falconindy on 2010-01-19
A new architecture? Incredibly unlikely. An x86 compatible? Less unlikely.

Strange... Wikipedia article doesn't mention [OpenGraphics](http://wiki.opengraphics.org/tiki-index.php).

---

### Post by Simian Man on 2010-01-19
There are a few.  The most successful one I know of is the OpenSPARC, which is quite nice.  The hardware is focused on throughput rather than single thread performance, so it wouldn't make a great desktop.

Honestly, it's tough to compete with x86 for general-purpose use.

---

### Post by Zoot7 on 2010-01-19
> **k64 said:**
> Will someone be willing to create a whole new CPU architecture that's open source? I'd certainly be pleased.
That's never going to happen I'd say. CPU's or CPU-like components like DSPs etc. tend to be rather central to most Electronic companies who make them, thus they're not going to "open" all their central components.
Besides x86 is the defacto standard in the Computing area, so a newcomer is quite unlikely. There is ARM mind you, but the only place ARM stands to compete is on Netbooks.

---

### Post by Icehuck on 2010-01-19
> **k64 said:**
> [http://en.wikipedia.org/wiki/Open_source_hardware](http://en.wikipedia.org/wiki/Open_source_hardware)

Sounds pretty ambitious. My question: Will someone be willing to create a whole new CPU architecture that's open source? I'd certainly be pleased.

Sure as long you pay for all my research and development costs. Also, please don't expect anything for at least 20 years. I won't be able to design hardware and architecture on anything you could afford in any reasonable amount of time.

---

### Post by phrostbyte on 2010-01-19
> **Simian Man said:**
> There are a few.  The most successful one I know of is the OpenSPARC, which is quite nice.  The hardware is focused on throughput rather than single thread performance, so it wouldn't make a great desktop.

Honestly, it's tough to compete with x86 for general-purpose use.

I would say it's tough to compete with Intel/AMD for general-purpose desktop use. The power of x86 processors has little to do with the x86 instruction set. In fact, x86 IMO quite terrible for *any* use. It's just because of Windows and closed source universe of x86 apps that Intel/AMD sticks with it.

Basically, the OP should replicate the billions of dollars of joint R&D AMD and Intel have accomplished and a multi-billion dollar fabrication plant. Then it really won't matter what instruction set you use, your processor will be pretty competitive. :) 

But first I think the Linux API driver generator should be completed. I still have some hardware that doesn't work on Linux ;)

---

### Post by k64 on 2010-01-19
I found out that Sun was creating an open source CPU with the SPARC architecture:

[http://www.sun.com/processors/opensparc/](http://www.sun.com/processors/opensparc/)

That's an open source CPU right there.

---

### Post by falconindy on 2010-01-19
Hmmmm, looks like a group called OpenCores ported the GNU toolchain to their platform [OpenRISC](http://en.wikipedia.org/wiki/OpenRISC).

Neither of these arch's are new and exciting though... they're understandably modeled after pre-existing instruction sets.

---

### Post by phrostbyte on 2010-01-19
> **falconindy said:**
> Hmmmm, looks like a group called OpenCores ported the GNU toolchain to their platform [OpenRISC](http://en.wikipedia.org/wiki/OpenRISC).

Neither of these arch's are new and exciting though... they're understandably modeled after pre-existing instruction sets.

There won't be much instruction set innovation until open source displaces closed source IMO. The big chip makers don't want to change stuff that could possibly break apps and lose customers.

---

### Post by Simian Man on 2010-01-19
> **phrostbyte said:**
> Uh.. I would say it's tough to compete with Intel/AMD for general-purpose desktop use. The power of x86 processors has little to do with the x86 instruction set.

Not really.  It's tough to compete with x86, not because of the strength of the design, but because of the amount of lock-in it has.  There is a LOT of software written/compiled for x86 and switching to something else would be infeasible for most users - us Open Source would be OK with it though ;).

x86 sucks monkey-balls, don't get me wrong, but the problems with it are mostly solved problems that never were never really as serious as the backwards-compatibility problem.

---

### Post by phrostbyte on 2010-01-19
> **Simian Man said:**
> Not really.  It's tough to compete with x86, not because of the strength of the design, but because of the amount of lock-in it has.  There is a LOT of software written/compiled for x86 and switching to something else would be infeasible for most users - us Open Source would be OK with it though ;).

x86 sucks monkey-balls, don't get me wrong, but the problems with it are mostly solved problems that never were never really as serious as the backwards-compatibility problem.

++

---

### Post by Simian Man on 2010-01-19
> **Simian Man said:**
> There are a few.  The most successful one I know of is the OpenSPARC, which is quite nice.  The hardware is focused on throughput rather than single thread performance, so it wouldn't make a great desktop.

> **k64 said:**
> I found out that Sun was creating an open source CPU with the SPARC architecture:

[http://www.sun.com/processors/opensparc/](http://www.sun.com/processors/opensparc/)

That's an open source CPU right there.

Wow, where did you hear about that?  It sounds cool :).

---

### Post by Frak on 2010-01-19
> **k64 said:**
> I found out that Sun was creating an open source CPU with the SPARC architecture:

[http://www.sun.com/processors/opensparc/](http://www.sun.com/processors/opensparc/)

That's an open source CPU right there.
It's good for servers and... servers. Terrible for Desktop systems.

---

### Post by k64 on 2010-01-19
If someone did create an open source architecture it would be nice if they ported ALL GNU/Linux apps, including the GUI, to it. That way, all apps that work with Linux (that are open source) will be able to work with the new architecture (There are alternatives to proprietary ones - Openoffice.org for M$O, Chrome and Firefox for IE, Audacity for GarageBand, MythTV for WinMC, GNUCash for Quicken and TurboTax, Ubuntu Help Center for Windows Help and Support, you name it).

There's also some software you can't get proprietary, such as package managers.

---

### Post by Frak on 2010-01-19
> **k64 said:**
> If someone did create an open source architecture it would be nice if they ported ALL GNU/Linux apps, including the GUI, to it. That way, all apps that work with Linux (that are open source) will be able to work with the new architecture (There are alternatives to proprietary ones - Openoffice.org for M$O, Chrome and Firefox for IE, Audacity for GarageBand, MythTV for WinMC, GNUCash for Quicken and TurboTax, Ubuntu Help Center for Windows Help and Support, you name it).

There's also some software you can't get proprietary, such as package managers.
Who would pay for the development?
Who would buy the resulting product?
Who would port it?
What is M$O?

---

### Post by lisati on 2010-01-19
Interesting concept. I wonder how much of any new architecture will be inspired by existing architectures, and how different it will end up being.

---

### Post by Simian Man on 2010-01-19
> **k64 said:**
> If someone did create an open source architecture it would be nice if they ported ALL GNU/Linux apps, including the GUI, to it. That way, all apps that work with Linux (that are open source) will be able to work with the new architecture (There are alternatives to proprietary ones - Openoffice.org for M$O, Chrome and Firefox for IE, Audacity for GarageBand, MythTV for WinMC, GNUCash for Quicken and TurboTax, Ubuntu Help Center for Windows Help and Support, you name it).

You don't really have to "port" all Linux apps to an architecture.  For the most part, you just have to port GCC and binutils, and compile the rest of whatever you want for that.  You can already install Linux on virtually every architecture under the sun - including OpenSPARC.

---

### Post by Simian Man on 2010-01-19
> **lisati said:**
> Interesting concept. I wonder how much of any new architecture will be inspired by existing architectures, and how different it will end up being.

There are different "families" of architectures.  One of the first is known as Complex Instruction Set (CISC).  These have very complicated operations available in the architecture which make it very difficult to implement efficiently.  Intel's x86 architecture is the only member of this family that hasn't died like it should have.  Others include the Vax and PDP-11 which is the first architecture Unix was developed for IIRC.

After that came Reduced Instruction Set (RISC) machines.  These have a much simpler format and small set of operations.  This allows them to be implemented more efficiently.  Mips, Sparc, Arm and Alpha are in this category.  IBM's Power architecture is sort of a hybrid between CISC and RISC.  Pretty much all of these architectures are extremely similar.

Those two families pretty much dominate the architectures you will find in traditional computers.  Another notable one is VLIW which is *much* different than those others, but is generally confined to special, embedded devices like printer drivers.  There are a lot of other ones that are, so far, mostly confined to research.  There just hasn't been enough of a reason to abandon traditional architectures yet as none of the new ones have trumped them in the way that RISC made CISC obsolete.

---

### Post by lisati on 2010-01-19
> **Simian Man said:**
> There are different "families" of architectures.  One of the first is known as Complex Instruction Set (CISC).  These have very complicated operations available in the architecture which **make it very difficult to implement efficiently**.  Intel's x86 architecture is the only member of this family that hasn't died like it should have.  Others include the Vax and PDP-11 which is the first architecture Unix was developed for IIRC.


True! Althought not exactly related: In the minimal reading I've done on optimizing ASM code, I find it almost counter-intuitive that a perfectly good optimization for loops on the 8086/8088 (replacing DEC CX & JCXNZ with LOOP) is less than optimal on newer CPUs....

---

### Post by BuffaloX on 2010-01-19
> **Simian Man said:**
> Not really.  It's tough to compete with x86, not because of the strength of the design, but because of the amount of lock-in it has.  There is a LOT of software written/compiled for x86 and switching to something else would be infeasible for most users - us Open Source would be OK with it though ;).

x86 sucks monkey-balls, don't get me wrong, but the problems with it are mostly solved problems that never were never really as serious as the backwards-compatibility problem.

I was about to point this out as an answer to your first post.
The only reason X86 is still around is because of proprietary software IMO.

I made a pretty math intensive app back in the 486 days, and wanted to speed up the math.
I had 3 books on x86 assembly, but none had anything on programming math on it. Some of them even postulated it wasn't worth the bother, since modern compilers optimized very well for math instructions.

Yeah right. :^o

Then I found a free PDF book on the net, describing x86 programming in much more detail than any of the books I'd paid 50-80$ for each!

Turned out the calculation were more than twice as fast as when compiled with Borland C++ which was one of the best optimizing compilers of the time. The calculations was even on 80 bit precision, which probably have the least speed gain from assembly!

After that experience I was so disgusted with X86 assembly that I have never touched it again, also I have never bought a programming book since.

---

### Post by lostinxlation on 2010-01-19
If my memory serves, there was a project called OpenCore about 10 years ago. It was a project that develop free hardwares and I thought CPU development was also a part of the plan as well as other ASIC hardwares. I don't know what happened to that.
 
The problem is unlike software, hardware costs money to manufacture. You can go with FPGA, but you can't put the enough logic in it, the delay sucks, pin count is limited, and memory speed sucks too. If you need a highend CPU, the internal memories such as cache, register files, TLB. reservation station. etc. etc. have to be designed by agressive circuits for speed. You can't do that on FPGA, therefore you have to go custom chips, which costs millions for manufacturing. Obviously it's not something that some volunteer communities want to take. 
May be some brave companies can throw the money on it, but remember these companies already gave up the CPU. There are a numerous  companies that have developed CPUs, but now only Intel and AMD(and Sun/IBM) remain in the mass market.

---

### Post by lostinxlation on 2010-01-20
> **k64 said:**
> I found out that Sun was creating an open source CPU with the SPARC architecture:
 
[http://www.sun.com/processors/opensparc/](http://www.sun.com/processors/opensparc/)
 
That's an open source CPU right there.
 
I'd wonder they also provide IPs like memories, high speed execution units, PLLs and IO cells. The difficult part of CPU design is not logic itself, but making it faster which involves circuit designs of high speed memories and execution units.

---

### Post by DeadSuperHero on 2010-01-20
For what it is worth, PowerPC is open last time I checked, at least to a [degree]("http://apple.slashdot.org/article.pl?sid=05/06/08/1957254").

---

