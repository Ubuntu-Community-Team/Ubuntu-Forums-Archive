---
title: "Questions about CPU architectures"
date: 2010-02-19
forum: The Cafe
---

### Post by blueshiftoverwatch on 2010-02-19
I have some random questions about CPU architectures.

I know that generally PowerPC can do more with less clock cycles than x86. But PPC is RISC while x86 (and x64) is CISC. Which means that RISC takes more clock cycles do to the same thing. But, CISC instructions often have to be broken down to smaller instructions. Which I would think would make it take up more clock cycles as well. But this doesn't seem to be the case from what I can tell.

I thought that RISC was always preferable to CISC as long as backwards compatibility was not an issue. After all, videogame consoles are significantly less powerful than desktop PC's but can run the same games that you'd have to buy a top notch PC to run. And most game consoles are RISC. Although you wouldn't want to run a general purpose OS on them, like Linux for PS2 because it'd be so horribly underpowered you'd never get anything done.

Why is PPC often compared to x86 but not x64. PPC was 64 bit and x86 is 32 bit. I've heard people say "PPC is a better architecutre than x86" but not x64.

Wouldn't the fact that x86 and especially x64 are designed to be backwards compatible with an instruction set that came out 30 or so years ago while PPC doesn't need to carry any of that baggage severely limit what x86 and x64 can do in comparison to PPC?

---

### Post by hessiess on 2010-02-19
The biggest problem with X86 is that its so complicated that it can only be implemented by creating a software emulator which runs on top of one or more RISC-ish hardware CPU cores. Such an implementation wastes a huge amount of CPU power running the emulator instead of executing actual instructions. RISC cpu's are almost always implemented without microcode, so are more efficient.

Another difference is the number of registers, X86 has very few registers in comparison to most RISC architectures. The more registers a CPU has, the more it can do without having to do a slow memory read/write.

There is nothing wrong with running a desktop OS on a RISC CPU and they are perfectly powerful enough to do general computing work. The problem here is that Microsoft dominates the desktop market with an OS that only runs on X86 and the IBM PC architecture, which is fundamentally outdated and absolutely packed with hacks that attempt to keep it somewhat up to date.

---

### Post by blueshiftoverwatch on 2010-02-19
> **hessiess said:**
> The biggest problem with X86 is that its so complicated that it can only be implemented by creating a software emulator which runs on top of one or more RISC-ish hardware CPU cores. Such an implementation wastes a huge amount of CPU power running the emulator instead of executing actual instructions. RISC cpu's are almost always implemented without microcode, so are more efficient.
So, it's not that RISC is necessarily better than CISC. It's just that in reality most RISC architectures aren't designed to carry a bunch of baggage like a CISC architecture like x86 is.

If a new non-x86 CISC based architecture was designed today could it be just as powerful as currently existing RISC architectures and even established CISC architectures like x64?
> **hessiess said:**
> Another difference is the number of registers, X86 has very few registers in comparison to most RISC architectures. The more registers a CPU has, the more it can do without having to do a slow memory read/write.
Wouldn't PowerPC (which is 64 bit) have the same number of registeras as x64 (which is also 64 bit)?
> **hessiess said:**
> There is nothing wrong with running a desktop OS on a RISC CPU and they are perfectly powerful enough to do general computing work.
I never said that RISC wasn't suitable for a desktop OS. I was just wondering why a RISC architecture like PPC is fine for running say Macintosh OS9 or OSX but another RISC architecture like the PS2 isn't good for running another desktop OS like Linux.

---

### Post by Simian Man on 2010-02-19
> **hessiess said:**
> The biggest problem with X86 is that its so complicated that it can only be implemented by creating a software emulator which runs on top of one or more RISC-ish hardware CPU cores. Such an implementation wastes a huge amount of CPU power running the emulator instead of executing actual instructions. RISC cpu's are almost always implemented without microcode, so are more efficient.
Not exactly.  There is no "software emulator" in x86 chips, they just decode the CISC instructions into microinstructions.  That's done in hardware with a small ROM.  From that point on, the hardware just interacts with the microcode.  It would technically be faster without that stage, but modern CPUs are so aggressively pipelined anyway that it wouldn't be a big deal.

Additionally modern chips will store the microcode in a trace cache/L1 IC directly, further reducing the complexity.

> **hessiess said:**
> Another difference is the number of registers, X86 has very few registers in comparison to most RISC architectures. The more registers a CPU has, the more it can do without having to do a slow memory read/write.
x86 has fewer architecturally-visible registers, but using out of order execution, it can use as many hardware registers as make sense then rename operands of instructions to these hardware registers.  Also x64 added a bunch of new architected registers as well.

> **hessiess said:**
> There is nothing wrong with running a desktop OS on a RISC CPU and they are perfectly powerful enough to do general computing work. The problem here is that Microsoft dominates the desktop market with an OS that only runs on X86 and the IBM PC architecture, which is fundamentally outdated and absolutely packed with hacks that attempt to keep it somewhat up to date.

x86 is a horrible, horrible architecture, but Intel has thrown so much engineering at it that implementing it efficiently is essentially a solved problem.

If we see a new architecture that is more efficient than x86, it will not be a RISC.  It will be something quite different like VLIW.

---

### Post by blueshiftoverwatch on 2010-02-19
> **Simian Man said:**
> If we see a new architecture that is more efficient than x86, it will not be a RISC.  It will be something quite different like VLIW.
Wow, I just looked that up on Wikipedia and I had no idea there was anything other than RISC and CISC.

---

### Post by hessiess on 2010-02-19
> **blueshiftoverwatch said:**
> 
Wouldn't PowerPC (which is 64 bit) have the same number of registeras as x64 (which is also 64 bit)?

A register is a small block of memory the size of the CPU's word. PPC has 64 registers (32 general, 32 floating point) x86 64 has 16 and plain x86 only has 8.

> 
I never said that RISC wasn't suitable for a desktop OS. I was just wondering why a RISC architecture like PPC is fine for running say Macintosh OS9 or OSX but another RISC architecture like the PS2 isn't good for running another desktop OS like Linux.

Simple answer, the PS2 was not designed to run desktop operating systems, its a game console. The original versions of the PS3 can run Linux, but it is slow because the GPU is locked out, meaning all graphics have to be done in software. The biggest problem with the design of these consoles for running desktop applications is the lack of memory available.

> 
Not exactly. There is no "software emulator" in x86 chips, they just decode the CISC instructions into microinstructions. That's done in hardware with a small ROM. From that point on, the hardware just interacts with the microcode. It would technically be faster without that stage, but modern CPUs are so aggressively pipelined anyway that it wouldn't be a big deal.


I was mealy trying to explain in a simple way that the hardware is not actually executing the instructions directly. Decoding the CISC instructions into microinstructions is dynamic recompilation.

> 
x86 is a horrible, horrible architecture, but Intel has thrown so much engineering at it that implementing it efficiently is essentially a solved problem.


But its still nowhere near as efficient as a cleanly designed, modern architecture such as ARM. X86 CPU's throw out a huge amount of heat whereas even the fastest ARM cores run cold with no heat sync at all and use a lot less power.

---

### Post by blueshiftoverwatch on 2010-02-20
> **hessiess said:**
> But its still nowhere near as efficient as a cleanly designed, modern architecture such as ARM. X86 CPU's throw out a huge amount of heat whereas even the fastest ARM cores run cold with no heat sync at all and use a lot less power.
When you say that ARM CPU's run cold with no heat sink, do you mean ARM CPU's that are in higher powered desktop type devices or supercomputers?

I've read that in the future CPU's will use fiber optic cables to transmit light instead of pulses of electricity, which will mean that there will be effectively no need to worry about overheating.

---

### Post by NoaHall on 2010-02-20
> **blueshiftoverwatch said:**
> 
I've read that in the future CPU's will use fiber optic cables to transmit light instead of pulses of electricity, which will mean that there will be effectively no need to worry about overheating.

Yes, in the very near future, at least for internal connections.

---

### Post by mustang on 2010-02-20
> **hessiess said:**
> 
But its still nowhere near as efficient as a cleanly designed, modern architecture such as ARM. X86 CPU's throw out a huge amount of heat whereas even the fastest ARM cores run cold with no heat sync at all and use a lot less power.

While this statement is true, it's also misleading. They both target different markets. Intel targets desktops and servers while ARM is more for mobile platforms. 

Performance wise, there is simply no comparison between an Intel CPU and an ARM based one; Intel will lap any ARM based CPU over and over.

---

### Post by blueshiftoverwatch on 2010-02-20
> **mustang said:**
> Performance wise, there is simply no comparison between an Intel CPU and an ARM based one; Intel will lap any ARM based CPU over and over.
Do you know of any articles that compare the various CPU architectures. Because I've talked to other people who've said that theirs no reason why an ARM based computer couldn't be just as powerful as an x86 or x64 based one. Theirs just no market for them due to the near monopoly of x86 based chips.

I think the TSUBAME supercomputer uses ARM, although I can't confirm it as Google isn't proving good results.

---

### Post by blueshiftoverwatch on 2010-02-20
I was just thinking. Since all that is usually required to port an application from one architecture over to another, why did x86 become the monopoly (sans PPC and ARM) in the computer market? Why couldn't some computer company develop a newer and more efficient architecture and the software development companies could simply just recompile their software for it.

---

### Post by NoaHall on 2010-02-20
> **blueshiftoverwatch said:**
> I was just thinking. Since all that is usually required to port an application from one architecture over to another, why did x86 become the monopoly (sans PPC and ARM) in the computer market? Why couldn't some computer company develop a newer and more efficient architecture and the software development companies could simply just recompile their software for it.

Long-story short - because it's not always that simple.

---

### Post by blueshiftoverwatch on 2010-02-20
> **NoaHall said:**
> Long-story short - because it's not always that simple.
Are that many applications written in architecture dependent assembly language that porting currently existing apps over to a new architecture would require too much re-programming?

---

### Post by baddog144 on 2010-02-20
> **NoaHall said:**
> Long-story short - because it's not always that simple.
Especially in the case of operating systems. It simply wouldn't catch on, for the most part I don't think, Microsoft probably would't be interested, and let's face it, that's a pretty big factor here.

---

### Post by Simian Man on 2010-02-21
> **blueshiftoverwatch said:**
> Do you know of any articles that compare the various CPU architectures. Because I've talked to other people who've said that theirs no reason why an ARM based computer couldn't be just as powerful as an x86 or x64 based one. Theirs just no market for them due to the near monopoly of x86 based chips.

An ARM-based processor could be just as fast as an x86-based one, but then it would have to use all of the tricks used by x86 processors: out of order execution, lots of registers and functional units, large caches, excessive speculation etc.  All of these allow modern processors to be fast, but kill energy-usage much more than x86's complicated decoding.

So if you made a high-performance, general-purpose processor that implemented the ARM architecture, it just wouldn't be much more energy-efficient than an x86-based one.

---

### Post by pbpersson on 2010-02-21
I lost interest in RISC when Apple dropped it and went to Intel.

Someone explain to me.....if the architectures are so different.....how Apple was able to move the Mac from Motorola chips to PowerPC chips to Intel chips and have everything still remain backwards compatible?

---

### Post by hessiess on 2010-02-21
> **pbpersson said:**
> I lost interest in RISC when Apple dropped it and went to Intel.

Someone explain to me.....if the architectures are so different.....how Apple was able to move the Mac from Motorola chips to PowerPC chips to Intel chips and have everything still remain backwards compatible?

They included an emulator for running software from the previous OS. And with OSX, universal binaries allowed 3rd party software to run on both X86 and PPC, by including two different versions of the software.

Cross architecture compatibility only rilley works with open source software.

---

### Post by hessiess on 2010-02-21
> **mustang said:**
> While this statement is true, it's also misleading. They both target different markets. Intel targets desktops and servers while ARM is more for mobile platforms. 

Performance wise, there is simply no comparison between an Intel CPU and an ARM based one; Intel will lap any ARM based CPU over and over.

But do general users actually need that much power, the vast majority of computers are massively overpowered for what they are actually used for and just run idle almost all of the time.

---

### Post by blueshiftoverwatch on 2010-02-21
> **Simian Man said:**
> An ARM-based processor could be just as fast as an x86-based one, but then it would have to use all of the tricks used by x86 processors: out of order execution, lots of registers and functional units, large caches, excessive speculation etc.  All of these allow modern processors to be fast, but kill energy-usage much more than x86's complicated decoding.

So if you made a high-performance, general-purpose processor that implemented the ARM architecture, it just wouldn't be much more energy-efficient than an x86-based one.
I thought that x86 (we are talking about all x86's right, including the current x64?) only had all of those hacks because it's been continually upgraded over the past 32 years. A newer processor like ARM wouldn't need all of the "tricks" that x86 uses to be as fast as it does because it was designed on sounder principals, I would assume.
> **hessiess said:**
> But do general users actually need that much power, the vast majority of computers are massively overpowered for what they are actually used for and just run idle almost all of the time.
All CPU's run idle or close to idle most of the time. But just because someone might write reports, browse the web, read email, or do any other order to low powered tasks 90% of the time doesn't' mean they don't need a powerful CPU. They might be playing a modern 3D videogame, encoding audio/video files, or doing any number of other things the other 10%. If everyone got a CPU that was designed to only do what they did most of the time we'd still all be using Pentium 4's. Not to mention that Windows 7 is extremely slow and bloated. So it needs a powerful CPU.

---

### Post by blueshiftoverwatch on 2010-02-21
edit: double post

---

### Post by mustang on 2010-03-13
> **hessiess said:**
> But do general users actually need that much power, the vast majority of computers are massively overpowered for what they are actually used for and just run idle almost all of the time.

I agree. The general user can get off fine without using the latest and greatest hardware. I'm not trying to criticize ARM in any way. I'm just saying ARM and Intel have two different audiences.

---

### Post by markbuntu on 2010-03-13
The big problem with x86 was that it was originally assembled for the 8 bit instruction set for the 8086 cpu. Everything after that was built on this primitive achitecture/assembler code. More assembler instructions were built into the chips and became available as the architecture progressed but there was a lot of kludgy stuff going on to keep backwards compatibility with the original instruction set. The basic hardware and assembler architecture was never reconfigured and new stuff just got piled on creating a very large and complicated instruction set that, depending on how the code was written, could cause huge differences in speed to accomplish the same tasks once it was assembled.

This is why Motorola came up with the RISC chips. It stands for Reduced Instruction Set Computer. Motorola vastly reduced the complexity of the chip and the number of available instructions, many of which were slow workarounds of old 86 architecture limitations and assembler problems or were never called anyway. IBM was quite enamored of the new RISC chips and the IBM OS2 operating system ran very well on them until it became a joint venture with Microsoft and the plug was pulled. 

Apple bought into the RISC chips because it could design its OS so it would not run on PCs and Windows could not run on the machines and Motorola needed a customer for the chips. For apple it was all about control. For Motorola it was about getting some return on their investment.

When AMD produced the first amd64 chips they abandoned a lot of the old x86 architecture. Since the new 64 bit architecture required a new assembler they could write it from scratch and abandon a lot of the old kludgy workarounds and at the same time make the assembler compatible with all the old x86 code. Intel was not able to move so quickly, being so invested in the old 86 architecture and trying to maintain backwards compatibility. Their first 64 bit chips were far slower than amd chips and they eventually abandoned that effort and moved to true 64 bit architecture and wrote a new assembler.

There was more than one reason why apple moved to a Unix type OS and pc chips. Motorola was in trouble and looked like it was going to stop RISC production or sell it off and it was becoming increasingly expensive to maintain a proprietary niche OS. So they basically made a BSD remix and ported everything over to PC architecture.

Now the big chip manufacturers have moved to 128 bit architecture and have been using them for while now in commercial and industrial applications. AMD will begin offering these new chips for consumer machines next year. The only OSs that can make use of them is linux and unix.

The big problem is that far to many applications are still stuck on 32 bit architecture, written in languages that require this. The days of writing user apps for single architecture and single OS are coming to an end. The new programming languages are architecture and OS agnostic.

Many linux applications have recently moved to 64 bit because the devs have adopted the new methods that make porting trivial but many users and devs are still convinced that they need 32 bit for their applications to work even though this is becoming less and less true. Users and devs need to get on board or be left behind.

---

### Post by NMFTM on 2010-04-24
> **markbuntu said:**
> Apple bought into the RISC chips because it could design its OS so it would not run on PCs and Windows could not run on the machines and Motorola needed a customer for the chips. For apple it was all about control. For Motorola it was about getting some return on their investment.
I read an article somewhere saying that the PowerPC chips had more instruction sets than the equivalent Pentium chips of the time. If we agree that Pentium = CISC and PowerPC has more instructions than a Pentium, than PowerPC can't legitimately be called RISC.
> **markbuntu said:**
> When AMD produced the first amd64 chips they abandoned a lot of the old x86 architecture.
How much of it was abandoned?
> **markbuntu said:**
> The big problem is that far to many applications are still stuck on 32 bit architecture...Many linux applications have recently moved to 64 bit...
I've noticed this as well. I have the x64 version of Windows 7 installed and it seems like 95% of my applications run in IA-32 compatibility mode. Wheras on Linux 95% of my applications run in native x64.

Even if most applications don't require 64 bits (like Pidgin or Firefox) to run faster. Wouldn't the fact that those applications require IA-32 libraries as well as the CPU having to run that app in IA-32 virtualization mode slow down overall performance?

---

### Post by mickie.kext on 2010-04-24
> **NMFTM said:**
> I read an article somewhere saying that the PowerPC chips had more instruction sets than the equivalent Pentium chips of the time. If we agree that Pentium = CISC and PowerPC has more instructions than a Pentium, than PowerPC can't legitimately be called RISC.


You most likely did not read it correctly, or article is false. POWER chips can do a lot **more instructions per cycle** than Intel chips, and that is exactly because instructions are simpler and there is less of them, so execution is quicker. CISC chips tend to have enormous number of complicated instructions, and for chip to be utilized completely, sofware has to be tuned for those instructions. For prime example of CISC processor, see IBM's z10 Mainframe processor. 

Intel and AMD today make RISC chips with RISC to CISC decoder in it, and that decoder has x86 ISA in it. Other parts of chip are plain RISC.

---

### Post by xir_ on 2010-04-24
> **markbuntu said:**
> 

Now the big chip manufacturers have moved to 128 bit architecture and have been using them for while now in commercial and industrial applications. AMD will begin offering these new chips for consumer machines next year. The only OSs that can make use of them is linux and unix.


Now this i would be interested in buying. 128 bit processors would really be a boost to my research, provided there is no FLOP degradation.

---

### Post by mickie.kext on 2010-04-24
I only now read this post, and most of this is fiction:
> **markbuntu said:**
> The big problem with x86 was that it was originally assembled for the 8 bit instruction set for the 8086 cpu. Everything after that was built on this primitive achitecture/assembler code. More assembler instructions were built into the chips and became available as the architecture progressed but there was a lot of kludgy stuff going on to keep backwards compatibility with the original instruction set. The basic hardware and assembler architecture was never reconfigured and new stuff just got piled on creating a very large and complicated instruction set that, depending on how the code was written, could cause huge differences in speed to accomplish the same tasks once it was assembled.

This part is true. I will skip other parts of the post which seems to be true.
> **markbuntu said:**
> This is why Motorola came up with the RISC chips. It stands for Reduced Instruction Set Computer. Motorola vastly reduced the complexity of the chip and the number of available instructions, many of which were slow workarounds of old 86 architecture limitations and assembler problems or were never called anyway. IBM was quite enamored of the new RISC chips and the IBM OS2 operating system ran very well on them until it became a joint venture with Microsoft and the plug was pulled. 
None of this is true.

1. Motorola did not "come up" with RISC. RISC researched at Berkley and commercial pioneers were MIPS Technologies and Sun Microsystems with its MIPS and SPARC designs respectively. Later IBM joined with its POWER chip. Earlier Motorola 86k chips were CISC. 

2. [POWER]("http://en.wikipedia.org/wiki/Power_Architecture") ISA is not invented by Motorola, it's IBM's product. Motorola got it when entered [AIM]("http://en.wikipedia.org/wiki/AIM_alliance") (Apple, IBM, Motorola) alliance.

3. [OS/2]("http://en.wikipedia.org/wiki/OS/2") was not made for POWER ISA, it is x86 OS. IBM ported it to POWER long after Microsoft puled away from OS/2.  


> **markbuntu said:**
> When AMD produced the first amd64 chips they abandoned a lot of the old x86 architecture. Since the new 64 bit architecture required a new assembler they could write it from scratch and abandon a lot of the old kludgy workarounds and at the same time make the assembler compatible with all the old x86 code. Intel was not able to move so quickly, being so invested in the old 86 architecture and trying to maintain backwards compatibility. Their first 64 bit chips were far slower than amd chips and they eventually abandoned that effort and moved to true 64 bit architecture and wrote a new assembler.

AMD did not abandoned practically any part of x86. They just extended it to 64 bits, same way Intel extended it from 8 to 16 and later from 16 to 32 bits. Off course, some of old 16 baggage is dropped when you run CPU in 64-bit mode, but it is still there when you run 32-bit mode. Also, x86_64 assembler is still very similar to x86_32. Basically the superset of it. Reason why Intel "did't move so quickly" is because they invested in the entirely new IA64 (a.k.a. [Itanium]("http://en.wikipedia.org/wiki/Itanium")) architecture which is was a flop. 

> **markbuntu said:**
> Now the big chip manufacturers have moved to 128 bit architecture and have been using them for while now in commercial and industrial applications. AMD will begin offering these new chips for consumer machines next year. The only OSs that can make use of them is linux and unix.

What? Source please! None of the chip makers "have moved to 128-bit" architectures. There is no valid announcements that anybody is working on 128-bit chips, and there is no ISA documents nor the work on compilers which would support such an architecture. If you think AMD Buldozer is 128-bit, then you are mistaken. It has 128-bit FPU (like most current chips), but ISA is still 64-bit. It is x86_64 chip like Phenom, no porting required. 

EDIT: Also, there is no need for 128-bit chips. Only reason for going 64-bit was 4GB memory limit. 64-bit memory limit is at 16 Exabytes, we are not even close.

> **markbuntu said:**
> The big problem is that far to many applications are still stuck on 32 bit architecture, written in languages that require this. The days of writing user apps for single architecture and single OS are coming to an end. The new programming languages are architecture and OS agnostic.

Like C was from 1970? Or Java from 1995? There will always be way to lock people in if people do not do not mind being locked-in. It people's fault, not technology's.

---

### Post by xir_ on 2010-04-25
> **mickie.kext said:**
> 
EDIT: Also, there is no need for 128-bit chips. Only reason for going 64-bit was 4GB memory limit. 64-bit memory limit is at 16 Exabytes, we are not even close.



Actually for science 128 bits would be very important for accuracy.  The ram aside we do tend to get into very very small numbers even in AU.

---

