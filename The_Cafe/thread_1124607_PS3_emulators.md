---
title: "PS3 emulators"
date: 2009-04-13
forum: The Cafe
---

### Post by StOoZ on 2009-04-13
Im not looking for one , nor for any other emulator , I just wondering why there are no PS3 emulators for PC out there?

seems kinda weird to me.

---

### Post by LowSky on 2009-04-13
Few Reasons, the Games are on Blu-Ray, which is still not fully cracked.

Blu-Ray support is horrible on linux, and for Windows not much better.

The games take up GB of space, most of which are at least 720P in video quality and HD sound.

the games run on a computer chip based pn the IBM PowerPC technology, so a x86 based processor couldn't even try to run the code without serious processing speed, most people dont have.

And thats just off the top of my head. There got ot more technical reasons

---

### Post by hessiess on 2009-04-13
The PS3 is extremely complicated hardware wise, it has an 8 core cell processor for example. Assuming that it would be possible to emulate it on current hardware, it would be *VERRY* slow. Hell, even PS2 emulation is still far from complete, eave Sony had problems implementing it on the PS3;)

---

### Post by StOoZ on 2009-04-13
so basically what you all are saying is that a PS3 processor is way stronger / faster than a regular nowadays processor?? (such as core 2 duo , quad ...)

---

### Post by Mehall on 2009-04-13
> **StOoZ said:**
> so basically what you all are saying is that a PS3 processor is way stronger / faster than a regular nowadays processor?? (such as core 2 duo , quad ...)

PPC has a better design. It;s been known for years and years, but it's easier to get people to make x86 stuff because of the lock-in between Intel and Microsoft. (Hell, Itanium is having an issue breaking that compatibility)

x86 is a horrid piece of design. current 32-bit and amd64 style 64 bit processors have backwards compatability right back to at least 16-bit, generally 8-bit (that's why you can run Win 3.11 on a current processor, and a 32-bit OS on a 64-bit processor, etc, etc, etc.)

PPC and others are much better ways of doing things, but Microsoft knows if it opens up the market to others, Linux is already ported to them, Windows would take too long, and not every Windows program would run on every architecture, so they locked us in. Intel helped too.

---

### Post by LowSky on 2009-04-13
> **Mehall said:**
> PPC and others are much better ways of doing things, but Microsoft knows if it opens up the market to others, Linux is already ported to them, Windows would take too long, and not every Windows program would run on every architecture, so they locked us in. Intel helped too.


This is a bad statement. It isn't that PPC is better but its different, so much so it share little design with current Intel type design that all x86 producers use. Mircosoft never supported the chip for many reasons, the main one being to keep IBM PC compatablity, as back in the day IBM was the company that everyone copied. Becaus ethe PC took off it became the defacto choice for Microsoft to design for. other chip creators like Motorola and later IBM used the PowerPC chipset to overcome the hurdles the x86 type processor had. This is why Apple's computer used to run these processors exclusively, until OS/X and Intel became part of Apple's Mac line.

Today the PPC chipset is used exclusively in the Nintendo Wii Xbox360 and PS3. the Wii being much less powered than the PS3. The PS3 chip is actually a marvel it was a 8-core chip(PS3 only uses 7 though) before Intel or AMD were marketing 4-cores to consumers.

---

### Post by Mehall on 2009-04-13
> **LowSky said:**
> This is a bad statement. It isn't that PPC is better but its different, so much so it share little design with current Intel type design that all x86 producers use. Mircosoft never supported the chip for many reasons, the main one being to keep IBM PC compatablity, as back in the day IBM was the company that everyone copied. Becaus ethe PC took off it became the defacto choice for Microsoft to design for. other chip creators like Motorola and later IBM used the PowerPC chipset to overcome the hurdles the x86 type processor had. This is why Apple's computer used to run these processors exclusively, until OS/X and Intel became part of Apple's Mac line.

Today the PPC chipset is used exclusively in the Nintendo Wii Xbox360 and PS3. the Wii being much less powered than the PS3. The PS3 chip is actually a marvel it was a 8-core chip(PS3 only uses 7 though) before Intel or AMD were marketing 4-cores to consumers.

The design, from an efficiency point of view, is much higher in PPC than in Intel architectures.

There ARE arguments for either side, not gonna deny that, but lets just say i386 and compatible are not the most efficient platforms. We're mostly stuck now, so it doesn't matter. (though it does in the server market where there are still RISC and ZISC and MISC alternatives, though most of these have died)

---

### Post by CharmyBee on 2009-04-13
> **LowSky said:**
>  The PS3 chip is actually a marvel it was a 8-core chip(PS3 only uses 7 though)

8 cores doesn't sound so much more than hype when the video chipset bottlenecks the capabilities and performance though, kinda like the PS2 being "a P3 700 times 3".

---

### Post by darrenn on 2009-04-13
You would need a extremely powerful computer to properly emulate a ps3. Not sure about how powerful exactly but maybe somebody else can take a educated guess. Plus most of the good games for ps3 have also been released for pc. So at this point not really a need for a ps3 emulator.

---

### Post by insane_alien on 2009-04-13
> **darrenn said:**
> You would need a extremely powerful computer to properly emulate a ps3. Not sure about how powerful exactly but maybe somebody else can take a educated guess. Plus most of the good games for ps3 have also been released for pc. So at this point not really a need for a ps3 emulator.

well, single core PPC emulators run about 100x slower. so with a 7 core ppc architecture 1000x slower wouldn't be too far off (the 7 cores plus overhead) and then you have to consider that it is likely a bit more complex so that could push it even slower.

a PS3 is clocked at 3.2GHz so an x86 would need something like 3.2THz (this is one of those situations that relies on clock speed as well as cores)

although this particular processor could take advantage of extra cores as it is itself a multi core processor. until we get octo-cores this will only add more computational overhead.

with 8 cores your still looking at 100x slower so thats 320GHz. still pretty unreasonable but we'll assume that 320GHz octocores are available.

so, now we've implemented the cell processor. do we have a PS3? no. theres more in a PS3 than that.

The graphics processor on a PS3 is equivalent to a graphics card on a PC with lots of stream processors. multi hundred core CPU's just don't exist but multi hundred core GPU's do. so if the emulator can be done in OpenCl or CUDA you can forget a proper emulation of the GPU.

and there's the network interface and audio. not so computationally expensive you can do it on remaining CPU core.

AND then you can get something like a usable PS3 emulator. and pleas note i've weighted my assumption in favour of emulating a PS3(assuming you can emulate the graphics on a graphics card with no additional modifications and still render it on screen that amazingly fast and core happy CPU's are available.)

as you can see it is a fair bit off and cheaper to just buy a PS3, or even several hundred.

---

### Post by mips on 2009-04-13
> **StOoZ said:**
> ...I just wondering why there are no PS3 emulators for PC out there?

seems kinda weird to me.

And I'm wondering why I have not seen any flying pigs yet?

Aint going to happen for a long time. Technology is to complex to emulate with current x86 hardware.

---

### Post by Izek on 2009-04-15
> **mips said:**
> Aint going to happen for a long time. Technology is to complex to emulate with current x86 hardware.

Yeah, you can barely run a PS2 Emulator smoothly as it is without a 3.0 GHz Processor or better (preferrably 2 cores or more.) Not many computers have that kind of speed at the moment. Especially not laptops.

---

### Post by toupeiro on 2009-04-15
Here's a longer explanation why you wont see PS3 emulation anytime soon.  Why longer?  because I'm bored, can't sleep, and feel like being long winded. ;)

PPC is much more advanced than x86, but I am careful with the word better.  If it were better, it would be the leading processor, but whether it be reasons of intellectual property, development difficulties, expense in manufacturing, or a combination of all of the above, it does not outsell x86.  Better is too vague.  It is, however, more advanced.

x86 technology has had its last real framework redesign with the 80386.  Everything from the first 80386 to the Nehalem is nothing more than the generational flow of the x86 design coupled with Moore's law and exdended registers.  Nothing truly revolutionary has happened in the x86 framework space since 1985.  The framework of the 80286 and 80386 were redesigned, whereas the 80486, the pentium (p5) etc etc, were extensions of what was done with the 80386, but cramming more things on the die like an FPU, and dual pipeline and eventually multiple cores, greatly due to Moore's law, but not necessarily due to any real framework restructure.  This isn't necessarily a bad thing.  If it rolls, don't reinvent the wheel, just make it roll faster...  Keep in mind that sticking multiple cores on a die is not necessarily what I mean by framework redesign.  an x86 core is an x86 core no matter how many you leverage from one die and one socket.  Maybe I have the wrong idea, but if you look at the lifeline of PowerPC, you will understand why I see x86 in this light.

PPC architecture, on the other hand, has RISC origins dating back to the IBM 801 chip in the 70's, and has scaled into anything from a MAC or Amiga to an RS6000 's and AS/400 Mainframes.  The PPC as we know it today is product of two RISC architectures and one hardware vendor and software developer: IBM's POWER1 architecture, Motorola's 68000 series architecture, and Apples .. bread and butter.  To really debate the differences would be a debate between RISC and CISC.  A good example of modern RISC would be a modern SPARC processor, whereas a good example of a modern CISC processor would be an Intel Nehalem (Core i7).  One could debate in many ways that CISC is more like RISC now, and in many ways, it is, but not in all ways.  One could look at a processor like the UltraSPARC T2 plus, which at 8 physical cores can do 64 simultaneous threads on one socket, scalability that cannot be met by the most powerful CISC x86 processor available today.  The best you could get out of a Nehalem would be 16 threads, 8 of those by way of hyper-threading. 

 An analogy I like to use to explain multithreading and cores would be a line at a costco or fryes.  Your threads would be lines of customers, your cores would be doors in and out of the store, your cores clock speed would be representing how fast the cashiers could move your line through the doors.  Nehalems hyperthreading would be those new self-checkout lines.  They seem fast, until you have an uncommon item to deal with. :)


So yeah, long winded explanation short, trying to emulate PPC architecture on x86 is going to prove a pretty significant challenge.  Just buy a PS3 :P  it'll be cheaper than the PC you would have to build to properly emulate one.

---

### Post by joshdudeha on 2009-04-15
Isn't that what PS3's were made for? ;)

---

### Post by toupeiro on 2009-04-15
> **joshdudeha said:**
> Isn't that what PS3's were made for? ;)

Egg-Zachary!

---

