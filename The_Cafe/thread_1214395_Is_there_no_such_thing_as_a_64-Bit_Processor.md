---
title: "Is there no such thing as a 64-Bit Processor?"
date: 2009-07-15
forum: The Cafe
---

### Post by Shibblet on 2009-07-15
I was talking to a friend of mine today, and he tells me that even though your processor may be "64-Bit" architecture, it only applies to memory addressing.

The processor still uses the standard x86 instruction set.

It made sense why Ubuntu comes in a x86_64 Version, as most Linux distros.

---

### Post by CharmyBee on 2009-07-15
Because of the x86's ancient hold on the market for over 25 years he might as well go backwards as to say there's no such thing as a 32-bit x86 processor either, since that's a progressive upgrade of 16-bit technology. Backwards compatibility was always a thing to maintain for the x86 since it was designed.

---

### Post by .Maleficus. on 2009-07-15
Sounds like your friend needs to check out this [Wikipedia]("http://en.wikipedia.org/wiki/X86-64") page.  64-bit processors do gain the ability to address 2^40 btyes (1TB) of physical memory and 2^48 bytes virtual but they also have other features that 32-bit processors do not have.


Edit:  And both of those numbers can be raised in future specs.

---

### Post by 3rdalbum on 2009-07-15
Intel did design the ia64 (Itanium) architecture which is meant to be a complete break from the past. It is not ia32 compatible. Surely that would be a fully-64-bit processor.

---

### Post by Pogeymanz on 2009-07-16
You friend is pretty much correct.

While 64-bit processors do exist, they are not the processors in your PC. "64-bit" processors in home computers are actually a hybrid design to retain backwards compatibility with 32-bit software and still include some of the benefits of 64-bit technology. A true 64-bit machine would not be able to run any 32-bit software.

---

### Post by HappyFeet on 2009-07-16
I don't know about anyone else, but I find 64 bit much better. It's seems normal at this point. At least with linux it does. When it comes to 64 bit, linux is leading the way to sane computing.

---

### Post by MaxIBoy on 2009-07-16
The main differences in the AMD64 architecture are increased address space (can handle more RAM,) more registers (which results in a major performance boost under the right circumstances,) and I think there may also be higher-precision floating-point operations available as well, but I could be wrong on that.


The actual instruction set itself probably doesn't scratch the tip of using even 16 bits (I.E. if you made a list of all the instructions, you'd probably need less than 16 place values if you were to count them in binary.)

---

### Post by sdlynx on 2009-07-16
> **Pogeymanz said:**
> You friend is pretty much correct.

While 64-bit processors do exist, they are not the processors in your PC. "64-bit" processors in home computers are actually a hybrid design to retain backwards compatibility with 32-bit software and still include some of the benefits of 64-bit technology. A true 64-bit machine would not be able to run any 32-bit software.

This seems to make sense.  I'm pretty sure x64 is only possible w/ multi core or processors, so maybe they could both be x86 and together that's x64 when using both together?

---

### Post by lisati on 2009-07-16
Here's another Wikipedia page that might be of interest: [http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

edit: there's probably better ways of thinking of 64-bit than in terms of two 32-bit machines side by side.

---

### Post by MaxIBoy on 2009-07-16
> **sdlynx said:**
> This seems to make sense.  I'm pretty sure x64 is only possible w/ multi core or processors, so maybe they could both be x86 and together that's x64 when using both together?Nope. (And I used to think the same thing.)

But basically what you said is that a car is really just two motorcycles glued together, and if you attach them together the combined total will move *exactly* twice as fast. 

Adding more cores to a CPU is like adding more seats to a car. Adding greater bit depth is like making each individual seat more roomy. And, you guessed it, when you eventually end up with a massive stretch limo, your top speed, cornering, and acceleration are going to suck, and your gas mileage is going to be even worse.

Adding more seats (cores) to the car makes it require more power, and it's more difficult to keep the engine cool. Also, the speed of the car itself is reduced. So if you want to get one person somewhere as fast as possible, pick something light and fast. If you've got a whole lot of people and don't want to make multiple trips, get a van or a bus.

---

### Post by lisati on 2009-07-16
> **MaxIBoy said:**
> Nope. (And I used to think the same thing.)

But basically what you said is that a car is really just two motorcycles glued together, and if you attach them together the combined total will move *exactly* twice as fast. 

Adding more cores to a CPU is like adding more seats to a car. Adding greater bit depth is like making each individual seat more roomy. And, you guessed it, when you eventually end up with a massive stretch limo, your top speed, cornering, and acceleration are going to suck, and your gas mileage is going to be even worse.

Nicely said. I was strugling to come up with a way of saying this, but was distracted in my thinking by how on the [8086]("http://en.wikipedia.org/wiki/8086")/[8088]("http://en.wikipedia.org/wiki/8088") the 16 bit CS register is combined with the 16-bit IP register to produce an effective 20-bit address.

---

### Post by phrostbyte on 2009-07-16
> **Shibblet said:**
> I was talking to a friend of mine today, and he tells me that even though your processor may be "64-Bit" architecture, it only applies to memory addressing.

The processor still uses the standard x86 instruction set.

It made sense why Ubuntu comes in a x86_64 Version, as most Linux distros.

He is wrong. x86-64 also supports 64-bit operations, and has 64-bit registers. It's not just an address bus.

For instance, in a 32-bit processor - the add instruction can at most add two 32-bit numbers numbers together. But in 64-bit, it can work with 64-bit numbers. 

This is not directly possible on 32-bit. If you want to add two numbers that are greater then ~4 billion, you need complicated algorithms and orders of magnitude more processor time to work. In 64-bit, it's a single instruction for numbers up to some obscene amount.

---

### Post by toupeiro on 2009-07-16
Edit bodhi.zazen: large graphic removed =)

[IMG]http://blogs.sun.com/hotnets/resource/sun-ultrasparc-t2-processor.jpg[/IMG]

[IMG]http://blogs.oracle.com/stevenChan/images/itanium.jpg[/IMG]

---

### Post by Grant A. on 2009-07-16
> **toupeiro said:**
> 
[IMG]http://blogs.sun.com/hotnets/resource/sun-ultrasparc-t2-processor.jpg[/IMG]

What instruction set does the UltraSPARC use?

Forgive me if this is too off-topic.

---

### Post by toupeiro on 2009-07-16
> **Grant A. said:**
> What instruction set does the UltraSPARC use?

Forgive me if this is too off-topic.

VIS instruction set.  RISC.

Edit:  VIS is more focused towards the UltraSPARC sparcs, which is really an extension to its core instruction set.  SPARC is also the name of the instruction set.  In this generation, it would be SPARC V9 according to Wikipedia.

---

### Post by Grant A. on 2009-07-16
> **toupeiro said:**
> VIS instruction set.  RISC.

Ah, thank you. :)

---

### Post by Shibblet on 2009-07-21
> **phrostbyte said:**
> He is wrong. x86-64 also supports 64-bit operations, and has 64-bit registers. It's not just an address bus.

For instance, in a 32-bit processor - the add instruction can at most add two 32-bit numbers numbers together. But in 64-bit, it can work with 64-bit numbers. 

This is not directly possible on 32-bit. If you want to add two numbers that are greater then ~4 billion, you need complicated algorithms and orders of magnitude more processor time to work. In 64-bit, it's a single instruction for numbers up to some obscene amount.

Right, I understand the benefits ofa 64 bit Processor.  But from what you're saying, the x86 instruction sets are still used.  

What it sounds like, is there is no such thing as a processor with ONLY 64-Bit instructions.  If there was, could you run Ubuntu or Windows on it?

---

### Post by Grant A. on 2009-07-21
> **Shibblet said:**
> Right, I understand the benefits ofa 64 bit Processor.  But from what you're saying, the x86 instruction sets are still used.  

What it sounds like, is there is no such thing as a processor with ONLY 64-Bit instructions.  If there was, could you run Ubuntu or Windows on it?

Toupeiro already posted two images of 64-bit only processors.

The first one is the Sun UltraSPARC, and the second one is the Intel Itanium.

> **toupeiro said:**
> 
[IMG]http://blogs.sun.com/hotnets/resource/sun-ultrasparc-t2-processor.jpg[/IMG]

[IMG]http://blogs.oracle.com/stevenChan/images/itanium.jpg[/IMG]

---

### Post by Shibblet on 2009-07-21
> **Grant A. said:**
> Toupeiro already posted two images of 64-bit only processors.

The first one is the Sun UltraSPARC, and the second one is the Intel Itanium.

Forgive me, I got lost in the ENORMOUS image of the SGI Workstation.  Want me to re-post it so everyone knows what I am talking about?  ;)

But, second question, still...  Can you run Ubuntu x86_64 or Windows XP, V, or 7 64-Bit on them?  Or do either of these OS's still require some x86 instructions?

---

### Post by Delever on 2009-07-21
> **Shibblet said:**
> Right, I understand the benefits ofa 64 bit Processor.  But from what you're saying, the x86 instruction sets are still used.  

What it sounds like, is there is no such thing as a processor with ONLY 64-Bit instructions.  If there was, could you run Ubuntu or Windows on it?

Why do you need "only" 64-bit? Do you always need to count things up to 18446744073709551616? If it counted MILISECONDS, that thing would cover more than entire age of Earth. I think 4294967296 for many things is more than enough.

---

### Post by Shibblet on 2009-07-21
> **Delever said:**
> Why do you need "only" 64-bit? Do you always need to count things up to 18446744073709551616? If it counted MILISECONDS, that thing would cover more than entire age of Earth. I think 4294967296 for many things is more than enough.

I didn't say I did.  I merely asked if there was such a thing.  Also since there is, would it run Ubuntu or any form of 64-Bit Windows.

---

### Post by Delever on 2009-07-21
> **Shibblet said:**
> I didn't say I did.  I merely asked if there was such a thing.  Also since there is, would it run Ubuntu or any form of 64-Bit Windows.

Well, as I read Wikipedia, Intel Itanium would be 64 bit processor, but as I read further, it also has instructions optimized for 32 bits too. And, judging from [this]("https://help.ubuntu.com/9.04/installation-guide/ia64/ch05s01.html"), you can install ubuntu there, but it may not be the easiest thing.

EDIT: here it is: [http://cdimage.ubuntu.com/ports/releases/9.04/release/](http://cdimage.ubuntu.com/ports/releases/9.04/release/)

---

### Post by hessiess on 2009-07-21
> **Shibblet said:**
> I didn't say I did.  I merely asked if there was such a thing.  Also since there is, would it run Ubuntu or any form of 64-Bit Windows.

The Linux kernel has bean ported to run on almost everything, The Ubuntu distro only supports 32/64 bit X86. Gentoo for example will run on SPARC and Itanium CPU's.

Windows server will run on the Itanium CPU, outer versions will not.

---

### Post by mmix on 2009-07-25
[[img]http://lh4.ggpht.com/_WeSmg3AsLq8/SSl1LMDmNBI/AAAAAAAAAD4/jO9TgbaqRS8/OpenSPARC_square_01.gif[/img]](http://opensparc.net/)

---

### Post by MaxIBoy on 2009-07-25
> **toupeiro said:**
> 
<snip>
So *that's* what Erwin looks like!

---

### Post by lawrence1l on 2009-08-04
I am on technical thin ice here, but I think the Ultrasparc is a legitimate 64-bit, but the application software is 32 bit, because the 64 bit programs require more memory, and HDD space, and the costs outweighed the advantages, at least that is what I remember reading in the Sun literature.  If I am wrong, please don't be too hard on me.  

I also think the Alpha is 64-bit, and suffered due to the lack of 64 bit application software.  I know there is a pretty active Alpha crowd out there, all of whom know more about it than I do.  Perhaps this will bring them out of the woodwork.
Larry

---

### Post by Shibblet on 2009-08-14
Well, then there is such a thing as a 64 bit processor, but it sounds like it's not available for home or personal use.

What would be the performance benefits, other than just memory addressing?

---

### Post by phrostbyte on 2009-08-14
> **Shibblet said:**
> Right, I understand the benefits ofa 64 bit Processor.  But from what you're saying, the x86 instruction sets are still used.  

What it sounds like, is there is no such thing as a processor with ONLY 64-Bit instructions.  If there was, could you run Ubuntu or Windows on it?

Well if you want to be like that, then there is no 32-bit Intel processor either, since the processor can work like an 8-bit processor too.

x86 is just an instruction set. It can work with many different bit size of address, data, and registers.

So yes I would say the current crop of processors are indeed "true 64-bit".

---

### Post by stwschool on 2009-08-14
This is the primary reason we need open-source. Processor manufacturers have been held to x86 because of the microsoft domination of the market. Windows won't work on anything  other than x86 and most of the software on it is closed source. The obvious advantage of the model of giving a customer the source is s/he can compile it for any processor. This is where linux kicks in. So, in order to advance our microprocessor designs, we need to switch to open-source, as that enables us to keep our software stack, while upgrading to bigger and better things. Perhaps this is why intel are pushing linux so hard (ie they feel they can push further ahead with a new technology and perhaps x86 has hit the wall)?

---

### Post by Dr. C on 2009-08-15
> **stwschool said:**
> This is the primary reason we need open-source. Processor manufacturers have been held to x86 because of the microsoft domination of the market. Windows won't work on anything  other than x86 and most of the software on it is closed source. The obvious advantage of the model of giving a customer the source is s/he can compile it for any processor. This is where linux kicks in. So, in order to advance our microprocessor designs, we need to switch to open-source, as that enables us to keep our software stack, while upgrading to bigger and better things. Perhaps this is why intel are pushing linux so hard (ie they feel they can push further ahead with a new technology and perhaps x86 has hit the wall)?

This is so true. The only real reason for backwards compatibility is  ***complied binaries*** which are what the propriety software base consists of. It is also the reason why porting GNU / Linux to ARM is simple but porting Windows 7 to ARM is not. While Microsoft can port Windows 7 to ARM it would loose that vast ecosystem of Windows applications and drivers that are the real strength of Windows.
 
Many people dual boot 64bit GNU / Linux and 32 bit Windows on that same machine, but hardly anyone does this the other way around; namely 32 bit GNU / Linux and 64bit Windows on the same machine. 

By the way a 20 year old Windows 3.0 binary runs perfectly fine on Windows 7 on a modern quad core processor. Try doing that with an ancient GNU / Linux binary

---

### Post by macogw on 2009-08-16
64bit processors can do 64bit math and 64bit addressing. *Some* 64bit architectures can run 32bit code (amd64) and some cannot (ia64).

---

### Post by samjh on 2009-08-16
Why the heck would anybody think that a 64-bit processor wouldn't be able to 32-bit programs?  A few posters have said it, and it's completely wrong.  Some 64-bit architectures won't run 32-bit programs, but the dominant 64-bit architecture on desktop PCs -- the AMD4 -- is 32-bit compatible, since it is an extension of i686.

Intel's 80486 and Pentium series were fully 32-bit, but capable of executing 16-bit software.  Similarly, processors built on the AMD64 architecture (x86_64, if you prefer) are fully 64-bit, but have the capability to run 32-bit software.

"Fully 64-bit" or "truly 64-bit", does not rule out 32-bit capability.  AMD64/x86_64 processors are 64-bit.  They just used the i686 architecture as a base.  That doesn't make its 64-bit status fake or incomplete.

> **Shibblet said:**
> I was talking to a friend of mine today, and he tells me that even though your processor may be "64-Bit" architecture, it only applies to memory addressing.

The processor still uses the standard x86 instruction set.

It made sense why Ubuntu comes in a x86_64 Version, as most Linux distros.
??????

If you're talking about AMD64/x86_64, then they INCLUDE the x86 instruction set.  Their instruction isn't made ENTIRELY of x86.  They actually do have 64-bit only instructions.

If you take an Assembly program written for x86 and attempt to assemble the code on a x86_64 without any modifications or different assembly options, it will most likely fail.  I learned that the hard way.

---

### Post by blueshiftoverwatch on 2009-08-16
> **stwschool said:**
> The obvious advantage of the model of giving a customer the source is s/he can compile it for any processor.
I might be wrong about this. But just because you have the source code for an application doesn't mean that you'll be able to compile it to run on any type of architecture. If the application wasn't developed to run on a certain kind of architecture you can't just download the source, compile, and expect it to work. At the very least you'd have to do some tinkering with the source code.
> **macogw said:**
> *Some* 64bit architectures can run 32bit code (amd64) and some cannot (ia64).
What exactly is the advantage of having a 64bit processor that isn't backwards compatible with 32bit applications?

---

### Post by hobo14 on 2009-08-17
> **MaxIBoy said:**
> Nope. (And I used to think the same thing.)

But basically what you said is that a car is really just two motorcycles glued together, and if you attach them together the combined total will move *exactly* twice as fast. 

Adding more cores to a CPU is like adding more seats to a car. Adding greater bit depth is like making each individual seat more roomy. And, you guessed it, when you eventually end up with a massive stretch limo, your top speed, cornering, and acceleration are going to suck, and your gas mileage is going to be even worse.

Adding more seats (cores) to the car makes it require more power, and it's more difficult to keep the engine cool. Also, the speed of the car itself is reduced. So if you want to get one person somewhere as fast as possible, pick something light and fast. If you've got a whole lot of people and don't want to make multiple trips, get a van or a bus.

Either I'm reading your post wrong, or you've written it wrong.
It sounds like you're saying multiple cores won't give a performance increase, which of course is absurd (assuming the software makes use of multiple cores).

A blanket claim that multi-cores use more power is also incorrect; besides the fact that it is easier(ie. cheaper)(for manufacturers) to get performance increases from multicores rather than sticking with single cores, they can also save power:
A single P4 Prescott averages about 103W, dual intel Core about 75W, and an UltraSparc T1 (8 cores) about 70W.

Don't go thinking *more cores = higher power consumption*


In keeping with your motorbike/car theme, a better metaphor would be to liken a single core processor to a Ducati, and multi-cores to several electric scooters; each one can basically do the same as the Ducati, but is simpler, smaller, more efficient, they can be used together on the same route or sent simultaneously on different routes, and together they offer better overall people moving performance.

---

### Post by toupeiro on 2009-08-17
1)  Sorry about the big SGI picture.  I posted it as I was leaving for the day at work, and my monitor resolution is 2560x1600.  I knew it was bigger than the other two, but it was apparently much bigger than I thought.  It was linked to illustrate MIPS as another 64-bit architecture.

2)  If you want a good analogy for where a high density multiple core chip, like a SPARC coolthreads chip, I think of it like an ultra efficient checker line at something like a costco.

A costco may have 8 or 16 lanes (cores) that can handle 128 or 256 items at the same time (multi-threading) across all the lanes.  It does not mean its more power hungry but it does mean that if you have a group of people not going to the first available lane (single-threading), that the overall impact of that transaction may not be completed as quickly. as a lane optimized for moving single lines like people bagging your items and taking them to your car (larger pools of cache per core for single/dual core single-threaded operations = better single threaded performance.)

Where 64-bit comes in is the ability to efficiently address workloads like this.  When you start talking about RAM quantities in 32GB 64GB, or 128GB of ram and multi-threading, 32-bit computing just doesn't have the yield 64-bit does.  The reason you don't see them in desktops typically is simple, its rarely needed in desktop computing.  VERY few desktop users have the IO demands to exclusively tie up this kind of resource.  And no, the biggest baddest game on the shelf couldn't do it either. :P

---

### Post by macogw on 2009-08-17
> **blueshiftoverwatch said:**
> 
What exactly is the advantage of having a 64bit processor that isn't backwards compatible with 32bit applications?

Gives you a chance to overhaul things more thoroughly so you can do (example) more optimizations.

---

