---
title: "What's all the rage in 64 bit processors?"
date: 2010-08-10
forum: The Cafe
---

### Post by Scooter_X on 2010-08-10
I was just looking at the system 76 systems, they have the one called 'pangolin performance' and I think it looks sweet. I did notice it has a 64 bit processor (hence the only option of the 64 bit Lucid Lynx installation), and I wondered if I would even get it if it were 64 bit just because I hear of people (here and there, not all the time) having problems trying to get certain programs running on a 64 bit that were designed for a 32 bit. 

I was just reading wikipedia's article on the 64 bit processor and although I was able to sortof comprehend what I was reading, overall I didn't get it. I don't really see the advantage. Unless all you're doing is crunching numbers. Though I did see something about a 64 bit processor that also had a 32 bit processor inside of it, that's cool I guess. But still - what's the rage?

---

### Post by linux18 on 2010-08-10
all computers do is crunch numbers so 64 bit systems are faster. transcoding video, rendering, virtualization all greatly benefit from 64-bit. However you don'y need to use a 64 bit OS on a 64 bit cpu you can use 32bit if you want.

---

### Post by Dustin2128 on 2010-08-10
Hmm, I think you can utilize more RAM with 64 bit processors.

---

### Post by linux18 on 2010-08-10
> **Dustin2128 said:**
> Hmm, I think you can utilize more RAM with 64 bit processors.
the PAE 32bit kernel supports 64GB

---

### Post by Cam42 on 2010-08-10
Right. But if you're using Windows, or a standard kernel, you can't use more than 4GB of memory.

---

### Post by FuturePilot on 2010-08-10
> **linux18 said:**
> the PAE 32bit kernel supports 64GB

PAE = dirty hack.

---

### Post by linux18 on 2010-08-10
> **FuturePilot said:**
> PAE = dirty hack.
so is linux

---

### Post by Bachstelze on 2010-08-11
IA32 is, to put it bluntly, a very stupid architecture.  It suffers from a lot of poor design choices, which make a lot of people's lives (especially compilers and OSes developers) much harder than it ought to be.  Maybe you don't see it as a user, but I can assure you that a lot of people would be extremely thankful if everyone just switched to x86-64. That alone is a good reason to push it IMO.

---

### Post by lisati on 2010-08-11
> **FuturePilot said:**
> PAE = dirty hack.

Um, I don't see a paper bag on my computer......

Wait... "[kludge]("http://en.wikipedia.org/wiki/Kludge")" would be a better word for what I was thinking of.

IMO Linux has grown and hopefully improved somewhat since its early days.

---

### Post by NMFTM on 2010-08-11
> **Scooter_X said:**
> bit just because I hear of people (here and  there, not all the time) having problems trying to get certain programs  running on a 64 bit that were designed for a 32 bit.
The only 32 bit (IA-32 / x86) applications I've had problems getting to  run on a 64 bit (AMD64 / x86-64 / x64) system are console emulators /  virtual machines. Like NES, SNES, Genesis, etc. Because a lot of those  particular apps are coded in lower level languages that are more closely  tied to the CPU architecture and therefore less portable. And by "less  portable" I mean that even a simple recompile from source wouldn't get  them to run on the 64 bit architecture.
> **linux18 said:**
> all computers do is crunch numbers so 64 bit systems are faster
Yes and no, but for all intents and purposes: mostly yes.

64 bit processors are faster at handling higher end processes like gaming and video encoding that are compiled to run on 64 bit. But they're clock for clock, slightly slower at handling 32 bit applications. Because CPU's execute instructions and running 32 bit instructions on a 64 bit CPU is going to mean that the instructions are longer than what they'd be on a 32 bit CPU.

Although, I will say that I'm not 100% sure if that just applies to 32 bit apps running on a 64 bit OS on a 64 bit CPU. Or if they also apply to 32 bit applications running on a 32 bit OS on a 64 bit CPU. Maybe someone else can clarify this.

But, in reality a decent modern 64 bit CPU is probably going to be faster at running even 32 applications because the processors are faster (both because of a higher GHz and various other optimizations) that what a 32 bit CPU would be. Because with the exception of Intel Atom CPU's (and possibly AMD's equivalent CPU) they don't make 32 bit IA-32/x86 CPU's for home computers anymore.

---

### Post by MasterNetra on 2010-08-11
> **linux18 said:**
> the PAE 32bit kernel supports 64GB

Aye but Ubuntu 32bit isn't PAE. Its probably just simpler to system76 to toss on 64bit for their computers that have more then 3GBs of ram.

---

### Post by linux18 on 2010-08-11
> **MasterNetra said:**
> Aye but Ubuntu 32bit isn't PAE. Its probably just simpler to system76 to toss on 64bit for their computers that have more then 3GBs of ram.
but the pae kernel is in the repositories, so its an easy install

---

