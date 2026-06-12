---
title: "What's the best arch to have?"
date: 2009-10-07
forum: The Cafe
---

### Post by dragos240 on 2009-10-07
I've heard about x86, ARM, SH4, and others. I saw criticism about the x86 arch in one post in the 'windows users may be using linux 70% of the time' topic. So what architecture is best?

---

### Post by earthpigg on 2009-10-07
you should clarify that when you say 'arch' you are talking about CPU/motherboard Architecture and not Arch Linux.

> **dragos240 said:**
> So what architecture is best?

depends on the purpose.

for home desktop computing, it depends on your priorities.

---

### Post by murderslastcrow on 2009-10-07
Depends on what you mean by best. high-scale PowerPC processors and 64-bit architectures offer a lot of added speed and 64-bit handles processes with better multi-threading techniques. 64-bit at the same speed as the equivalent PowerPC takes up less energy, I think.

Also, if you're going for saving energy, ARM is the best for this process as far as I know. That's why so many netbooks/UMPCs/MIDs have ARM processors.

Also, 32-bit isn't BAD, but it's been around for such a long time... I think the Atom processors and Windows not having many 64-bit ports are the main reason 32-bit is still so big. Oh, and with Linux there's little reason to upgrade your PC, anyway, so that could be contributing to it.

I'm not big on computer science, though- I'd do your research. Google and Wikipedia are often quite reliable.

---

### Post by steev182 on 2009-10-07
This is quite a nice Arch:

[IMG]http://www.nps.gov/jeff/images/gateway_arch2.jpg[/IMG]

5 internets to the first facepalm image in the next minute ;)

---

### Post by dragos240 on 2009-10-07
[IMG]http://scienceblogs.com/insolence/facepalm.jpg[/IMG]

---

### Post by steev182 on 2009-10-07
:D i love this place

---

### Post by SomeGuyDude on 2009-10-07
> **steev182 said:**
> 5 internets to the first facepalm image in the next minute ;)

[IMG]http://imgur.com/JdZA1.jpg[/IMG]

---

### Post by dragos240 on 2009-10-07
Too late man.

---

### Post by wojox on 2009-10-07
[IMG]http://cdn0.knowyourmeme.com/i/6512/original/DoubleFacePalm.jpg[/IMG]

---

### Post by Xbehave on 2009-10-07
> **earthpigg said:**
> you should clarify that when you say 'arch' you are talking about CPU/motherboard Architecture and not Arch Linux.
No need, we are on **UBUNTU** forums, it was quite clear from the post.

While x86 is a lame arch, it has the most advanced chips so it will be hard to get the performance you are used to for a desktop/laptop on anything else.
x86_64 is slightly better than x86 because of the bigger addressspace (among otherthings), 
ARM (or any risc arch) is much more efficient than x86, however even most successful competitor to x86 (PPC) simply could not keep up.

Where ARM really wins is anywhere you don't want power or efficiencies is more important:
[LIST]
[*]Phones
[*]TVs
[*]Always on devices
[/LIST] 

Alternatively in a few years with enough chips on a board an ARM based board will have enough power to run a standard desktop (as of now, +high def video decoding), while being much more power efficient.

---

### Post by sideaway on 2009-10-07
ARM is nice. But doesn't have the brute force of x86... It totally depends on your needs, if there was 'one arch to rule them all'... we'd have one that rules them all. But we don't, so therer is no 'best' arch. But +1 for ARCH in netbooks, now that has potential.

---

### Post by kavon89 on 2009-10-07
The Z80 architecture is definitely on the cutting edge of computing at the moment. :)

I've always thought SPARC is quite good though, anyone have thoughts on that?

---

### Post by RiceMonster on 2009-10-07
> **kavon89 said:**
> The Z80 architecture is definitely on the cutting edge of computing at the moment. :)

I've always thought SPARC is quite good though, anyone have thoughts on that?

Last I heard SPARC doesn't have many advantages over intel architectures any-more, and it's still more expensive. I'm not an expert in this area though.

---

### Post by Frak on 2009-10-07
Intel. Compatible with more software than any other Arch.

---

### Post by Eisenwinter on 2009-10-08
> **Frak said:**
> Intel. Compatible with more software than any other Arch.
If you use this comparsion, then Windows is the best operating system there is.

---

### Post by jespdj on 2009-10-08
> **murderslastcrow said:**
> Depends on what you mean by best. high-scale PowerPC processors and 64-bit architectures offer a lot of added speed and 64-bit handles processes with better multi-threading techniques. 64-bit at the same speed as the equivalent PowerPC takes up less energy, I think.
There is a reason why Apple switched from PowerPC CPUs to Intel CPUs in 2006 - because the PowerPC CPUs were not keeping up the rapid development in processing speed like the Intel CPUs.

I don't believe your information about how fast and efficient PowerPC is compared to x86 is relevant anymore.

---

### Post by Xbehave on 2009-10-08
> **jespdj said:**
> There is a reason why Apple switched from PowerPC CPUs to Intel CPUs in 2006 - because the PowerPC CPUs were not keeping up the rapid development in processing speed like the Intel CPUs.
There was also marketing (intel had spread the [megahertz myth]("http://en.wikipedia.org/wiki/Megahertz_myth")) and windows compatibility. TBH I  agree that ppc lagged behind, however given the success of the xbox360, it was defiantly not an insurmountable gap.

---

### Post by koshatnik on 2009-10-08
> **steev182 said:**
> This is quite a nice Arch:

[IMG]http://www.nps.gov/jeff/images/gateway_arch2.jpg[/IMG]

5 internets to the first facepalm image in the next minute ;)

Nice arch.

---

### Post by praveesh on 2009-10-08
I was confused by the caption of this thread.

---

### Post by openfly on 2009-10-08
Hands down the best arch, is the flying buttress.

---

### Post by Simian Man on 2009-10-08
There's a difference between an architecture and a micro-architecture.  The architecture is the instruction set, register conventions and other details that form the "pact" between software and hardware. x86 is the worst, most convoluted architecture in common usage by far.

A micro-architecture, on the other hand, is an implementation of an architecture, and the best micro-architectures are made for the x86 architecture.  They do this not *because* of the design of x86, but *in spite of* it.  In fact most all of an Intel pipeline works on "micro instructions" which are nothing like real x86 codes, but much closer to the Risc instructions of Sparc and Arm.  Basically Intel through a lot of money into working around their abomination of an ISA in order to keep backwards compatibility.

Where alternative architectures are able to work well is in areas where backwards compatibility doesn't matter like consoles and embedded systems.

---

### Post by openfly on 2009-10-08
> **Simian Man said:**
> There's a difference between an architecture and a micro-architecture.  The architecture is the instruction set, register conventions and other details that form the "pact" between software and hardware. x86 is the worst, most convoluted architecture in common usage by far.

A micro-architecture, on the other hand, is an implementation of an architecture, and the best micro-architectures are made for the x86 architecture.  They do this not *because* of the design of x86, but *in spite of* it.  In fact most all of an Intel pipeline works on "micro instructions" which are nothing like real x86 codes, but much closer to the Risc instructions of Sparc and Arm.  Basically Intel through a lot of money into working around their abomination of an ISA in order to keep backwards compatibility.

Where alternative architectures are able to work well is in areas where backwards compatibility doesn't matter like consoles and embedded systems.

To quote two of the IEEE community's most recognized authorities on the matter...

[Quote="Kate Libby"]
Indeed. RISC architecture is gonna change everything.
[/quote]

[QUOTE="Dade Murphy"]
Yeah. RISC is good.
[/QUOTE]

---

### Post by Frak on 2009-10-08
> **Eisenwinter said:**
> If you use this comparsion, then Windows is the best operating system there is.

For the mass population, yes.

> **jespdj said:**
> There is a reason why Apple switched from PowerPC CPUs to Intel CPUs in 2006 - because the PowerPC CPUs were not keeping up the rapid development in processing speed like the Intel CPUs.

I don't believe your information about how fast and efficient PowerPC is compared to x86 is relevant anymore.

My G5 PPC (dual core) can smoke just about any C2D if the instruction sets are actually used correctly.

---

### Post by dragos240 on 2009-10-08
What about SH4? SH processors rock :p

---

