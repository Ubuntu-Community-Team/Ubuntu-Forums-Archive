---
title: "x86 best for servers?"
date: 2006-07-28
forum: Server Platforms
---

### Post by commodore on 2006-07-28
I don't know much about servers. I have never built nor administrated servers but today I found this page on sun.com:
[http://www.sun.com/servers/x64/x4600/](http://www.sun.com/servers/x64/x4600/)
At the left there's a benchmark which shows that Sun Fire X4600 is the fastest server in the world. But it runs a f**king Opteron! I hoped that servers have something better than x86. There's so many RISC stuff. And Sun has SPARC. Why do they make SPARCs and POWERs at all when x86 is the best?

---

### Post by Lord Illidan on 2006-07-28
Speed doesn't neccessarily mean the best. And the benchmark compared Sun's server to other companies server, not to SPARC, etc.

Remember that a server also needs to be reliable and stuff like that.

---

### Post by LordHunter317 on 2006-07-28
And Woodcrest crushes Opteron.

There's a few places where IA-32/x86_64 isn't optimum, but those areas are steadily receeding.  Basically all that's left these days are:[list][*]Mainframes, where CPU speed is irrelevant[*]HPC, where floating is critical[*]Large single-system boxes, like Sun F15Ks and other machines for tasks that need a lot of CPUs in one image.[/list]

---

### Post by commodore on 2006-07-29
It's so sad I'm going to cry :(

:D

Will Cell bring anything new into this? Do servers need that vector stuff?

---

### Post by LordHunter317 on 2006-07-29
By and large, no.  HPC-only, and it's not clear yet that IBM will actually position Cell proper to be a serious HPC competitor.  They may use Cell-tech, however.

---

### Post by commodore on 2006-09-05
I read that K6 was actually a RISC processor. It translated x86 instructions to RISC instructions. The same idea was used in Intel's P6 (Pentium III basically) and the new Core Duo processors are based on P6. So RISC does rule. Do the latest AMD processors use this? Can more speed be gained by removing the translator and running pure RISC instructions? It would be great if people would be able to drop x86.

---

### Post by alecjw on 2006-09-05
Plain HTTP servers don't need to be fast at all. They can be something you pulled out of a skip (but it needs to look nice and shiny). However, anything with ASP/PHP etc on it needs to be goddamned fast. If you know what sort of PC you need to compile software, you might understand. Server side scripting is like compiling. I thought that processor architectures are just different and that none are better than another.

---

### Post by inthewayboy on 2006-09-06
Was the K6 a true RISC CPU? I don't think so, but I could be wrong. I do remember hearing those terms thrown around, but I believe it's RISC in the sense that it supports and translates to it, but it isn't a true RISC CPU. 

From what I remember the Motorola/IBM PowerPC CPU's were the last major RISC CPU's being made, and since Apple canned those last year I don't see much play from them in the future.

I think you'll continue to see x86 for some time...it's not really the hardware that is the issue, it's converting all the software over to a new type that is a problem. Sure there are various flavors of linux (And even old WinNT4) that run on other platforms but the large majority is x86. For very specialized servers/software x86 may indeed not rule, but I doubt I will be seeing/supporting those for sometime.

---

### Post by inthewayboy on 2006-09-06
Oh, I and don't think we'll see Cell anytime soon...remember the PS2? Sony was making it sound like they would roll out these amazing workstations and such based on it and I can't say I ever heard of one...of course IBM might push Cell forward.

---

### Post by commodore on 2006-09-11
PowerPC is based on the POWER technology which is still very active but not that much in the desktop market anymore.

---

### Post by Glut on 2006-09-12
> **commodore said:**
> I read that K6 was actually a RISC processor. It translated x86 instructions to RISC instructions. The same idea was used in Intel's P6 (Pentium III basically) and the new Core Duo processors are based on P6. So RISC does rule. Do the latest AMD processors use this? Can more speed be gained by removing the translator and running pure RISC instructions? It would be great if people would be able to drop x86.

> **inthewayboy said:**
> Was the K6 a true RISC CPU? I don't think so, but I could be wrong. I do remember hearing those terms thrown around, but I believe it's RISC in the sense that it supports and translates to it, but it isn't a true RISC CPU. 

From what I remember the Motorola/IBM PowerPC CPU's were the last major RISC CPU's being made, and since Apple canned those last year I don't see much play from them in the future.

Modern x86 CPUs both AMD and Intel (VIA doesn't count for much :-)
have been effectively RISC since the introduction of the Pentium. The CISC instructions are broken down into 'micro-ops' and then those micro-ops are executed. This is, of course, simplification of: [http://www.csse.monash.edu.au/~carlo/SYSTEMS/GigaHz-CPU-0400.htm](http://www.csse.monash.edu.au/~carlo/SYSTEMS/GigaHz-CPU-0400.htm) Dr Kopp's nicely detailed explanation. So they are no longer truely CISC, but not fully RISC either. 

Would the CPUs be faster without the instruction decode stage? Possibly a little. Not enough to give up backwards and even sidewards (AMD <-> Intel) compatibility. Remember Intel's tried the whole 'give up x86 for something faster (Itanium)' but for good reasons that failed dismally. 

x86 are incredibly fast for the price, we used to be a SPARC shop, but it's impossible to justify anymore (especially with Solaris on x86.)

---

