---
title: "Questions about x86, x64, and PPC"
date: 2010-01-11
forum: The Cafe
---

### Post by blueshiftoverwatch on 2010-01-11
Does anyone know of some good articles that compare and contrast the most popular CPU architectures (x86, x64, and PPC) but does so in a way that isn't overly technical. Yes, I realize that PPC isn't a real contender anymore. But there are still enough pre-Intel Mac's floating around that they're not totally irrelevant.

I'm interested in what their advantages and disadvantages are. It kind of seems like that in comparison to the cell/smart phone market the desktop PC market is fairly stagnant and theirs not a whole lot of innovation going on due to the need to remain backwards compatible with a lot of older apps. CPU's continue to get more and more powerful. But it's basically just finding ways to continually get more and more power out of a 30yo technology. And now that it's getting harder to do that they're just adding more cores. Compare that to the cell/smart phone industry where companies can take chances with a lot of radical new ideas because nobody cares if their old cell phone apps will be forwards compatible with their new cell phone.

---

### Post by phrostbyte on 2010-01-11
Don't know about any articles. But as someone who has had to do x86 assembly language programming.. I can tell you it's a terrible, unorganized, bloated instruction set that resembles a series of tacked on hacks. ARM and MIPS are far better, and even other CISC instruction sets like 68000 are better designed.

---

### Post by blueshiftoverwatch on 2010-01-11
> **phrostbyte said:**
> I can tell you it's a terrible, unorganized, bloated instruction set that resembles a series of tacked on hacks. ARM and MIPS are far better, and even other CISC instruction sets like 68000 are better designed.
Aren't ARM and MIPS only suitable for lower powered handheld or embedded devices?

---

### Post by phrostbyte on 2010-01-11
It's worth noting that there is no *actual* x86 architecture processors on the market, and haven't been that way for awhile. All processors that expose a x86 instruction set do so virtually, the internal opcodes of the processor (microcode) are vastly different.

---

### Post by FuturePilot on 2010-01-11
> **blueshiftoverwatch said:**
> Aren't ARM and MIPS only suitable for lower powered handheld or embedded devices?

[No]("http://www.engadget.com/2010/01/05/marvell-shows-off-an-odm-smartbook-thinner-than-strict-decency-p/")

---

### Post by phrostbyte on 2010-01-11
> **blueshiftoverwatch said:**
> Aren't ARM and MIPS only suitable for lower powered handheld or embedded devices?

No.

---

### Post by Frak on 2010-01-11
> **phrostbyte said:**
> Don't know about any articles. But as someone who has had to do x86 assembly language programming.. I can tell you it's a terrible, unorganized, bloated instruction set that resembles a series of tacked on hacks. ARM and MIPS are far better, and even other CISC instruction sets like 68000 are better designed.

This. I've also been a fan of PowerPC assembler due to its readability. (It almost reads like broken English)

> **blueshiftoverwatch said:**
> Aren't ARM and MIPS only suitable for lower powered handheld or embedded devices?

Nope. In fact, MIPS have been in some high powered devices, such as the Nintendo 64. ARM could very well be supercharged to meet current demands. The biggest issue is that there's no market for high-powered ARM devices.

---

### Post by juancarlospaco on 2010-01-11
x86 and X64 are the same architecture

---

### Post by NoaHall on 2010-01-11
> **juancarlospaco said:**
> x86 and X64 are the same architecture

No. X64 commonly refers to X86_64.

---

### Post by Frak on 2010-01-11
> **juancarlospaco said:**
> x86 and X64 are the same architecture
Not by a longshot.

---

### Post by blueshiftoverwatch on 2010-01-12
> **NoaHall said:**
> No. X64 commonly refers to X86_64.
I was talking to my computer teacher and he said that x64 was originally just 64 bit functionality tacked onto to the 32 bit x86 architecture. But at this point it's legitimately it's own architecture and just happened to be designed to be backwards compatible with x86.

---

### Post by Frak on 2010-01-12
> **blueshiftoverwatch said:**
> I was talking to my computer teacher and he said that x64 was originally just 64 bit functionality tacked onto to the 32 bit x86 architecture. But at this point it's legitimately it's own architecture and just happened to be designed to be backwards compatible with x86.
It's not backwards compatible.

---

### Post by blueshiftoverwatch on 2010-01-12
> **Frak said:**
> It's not backwards compatible.
How so? I can run 32 bit applications and OS's on my 64 bit processor.

---

### Post by Frak on 2010-01-12
> **blueshiftoverwatch said:**
> How so? I can run 32 bit applications and OS's on my 64 bit processor.
Because your processor is also a 32-bit processor. If you had an Itanium, for example, you wouldn't be able to run 32-bit applications without emulation.

---

### Post by blueshiftoverwatch on 2010-01-12
> **Frak said:**
> Because your processor is also a 32-bit processor. If you had an Itanium, for example, you wouldn't be able to run 32-bit applications without emulation.
So in reality an x64 processor isn't actually directly running 32 bit apps or OS's, it's just emulating the instruction sets necessary to run them, right?

Doesn't that mean that running a 32 bit OS on a 64 bit CPU would be slower than running it on a 32 bit CPU? Assuming both CPU's had the same specs in every other category.

---

### Post by Frak on 2010-01-12
> **blueshiftoverwatch said:**
> So in reality an x64 processor isn't actually directly running 32 bit apps or OS's, it's just emulating the instruction sets necessary to run them, right?

Doesn't that mean that running a 32 bit OS on a 64 bit CPU would be slower than running it on a 32 bit CPU? Assuming both CPU's had the same specs in every other category.
Yes. Running 32-bit code on a purely 64-bit processor would present a performance hit. The Linux kernel supports 32-bit emulation for Itaniums in the kernel. In my tests, it can hit around 90% native speed, which is good.

As for normal Intel's or AMD's that we run day-to-day, they are natively 32-bit with 64-bit extensions. When you run 32-bit apps on your C2D or AMD Athlon/Phenom, you are running it on the native 32-bit processor. An Itanium would use a feature in the Linux kernel that allows near-native 32-bit emulation.

---

### Post by 3rdalbum on 2010-01-12
> **Frak said:**
> Yes. Running 32-bit code on a purely 64-bit processor would present a performance hit. The Linux kernel supports 32-bit emulation for Itaniums in the kernel. In my tests, it can hit around 90% native speed, which is good...

 An Itanium would use a feature in the Linux kernel that allows near-native 32-bit emulation.

I'm a bit confused, sorry. Itanium is natively 64-bit. It's not a set of extensions, it's a full 64-bit instruction set. And it's not x86-compatible.

So how come there's 32-bit code for the Itanium instruction set? Shouldn't it all automatically be 64-bit?

---

### Post by Frak on 2010-01-12
> **3rdalbum said:**
> I'm a bit confused, sorry. Itanium is natively 64-bit. It's not a set of extensions, it's a full 64-bit instruction set. And it's not x86-compatible.

So how come there's 32-bit code for the Itanium instruction set? Shouldn't it all automatically be 64-bit?
**Emulation**

EDIT
And there's an instruction set (like the VT extensions current processors have) that helped speed up 32-bit emulation. Some Itaniums had a 32-bit processor on-board just in case 32-bit was needed.

---

### Post by hobo14 on 2010-01-12
> **blueshiftoverwatch said:**
> Aren't ARM and MIPS only suitable for lower powered handheld or embedded devices?

No.

For example, a [MIPS supercomputer]("http://sicortex.com/products/high_capability_system_sc5832") and an [ARM supercomputer]("http://vr-zone.com/articles/nvidia-tesla-powers-29th-most-powerful-supercomputer-in-the-world/6216.html").

There are also [quite a lot of ARM based netbooks being developed]("http://ubuntuforums.org/showthread.php?t=1377293"), mainly from small companies, but recently larger companies such as ASUS, HP and Lenovo have been moving that way too.

---

### Post by Xbehave on 2010-01-12
x86_64 is 64bit x86 and is backwards compatible (requires an instruction to change to 32bit mode but, much faster x86 processing than ia64)
ia64 is 64bit not-x86 and is not backwards compatible except through emulation
X64 is a confusing term wikipedia defaults it to X86_64 but with a note for people looking for ia64

Itanium = ia64
C2D/AMD Athlon 64/Phenom = x86_64
AMD athlon= x86

PPC was/is RISC, but has droped from mainstream use since apple switched to x86 (ironically a major user is now microsoft's xbox360). While IMO PPC (purely by virtue of being RISC) has a better design than x86, IBM+Motorola+apple could not afford to keep up with Intel+AMDs rate of progress in chip manufacturing (especially after c2d, became a success for laptops). Why RISC is better is best explained by wikipedia, but basically all chips are now RISC, but x86 chips have hardware level conversion to RISC, whereas true-RISC chips let the compiler use them as RISC chips directly so you (in theory anyway) get better optimization.

One trap people fall into when they think ARM sucks is the [Megahertz myth]("http://en.wikipedia.org/wiki/Megahertz_myth") (A lie^H marketing ploy from intel that made their chips seam better), and forgetting that ARM boards tend to contain dedicated chips for various functions, so a 'slow' arm board can handle things like hd video or dual 3D monitors no problem (basically like having a decent graphics card on the motherboard, but without the powerconsumption)

---

### Post by blueshiftoverwatch on 2010-01-12
> **Frak said:**
> Yes. Running 32-bit code on a purely 64-bit processor would present a performance hit. The Linux kernel supports 32-bit emulation for Itaniums in the kernel. In my tests, it can hit around 90% native speed, which is good.
Of course, that was just theoretically. In reality, since all or almost all serious new processors for desktop computing are 64 bit at this point and the clock speed and other attributes of the CPU's are getting better. The fact that it has to emulate 32 bit would probably be more than made up for by the fact that the CPU it's self is generally faster, right?
> **Frak said:**
> As for normal Intel's or AMD's that we run day-to-day, they are natively 32-bit with 64-bit extensions. When you run 32-bit apps on your C2D or AMD Athlon/Phenom, you are running it on the native 32-bit processor. An Itanium would use a feature in the Linux kernel that allows near-native 32-bit emulation.
That doesn't sound like a good thing. But I guess Ext3 was basically Ext2 with journaling slapped on and it was a very good file system for it's time.

So, how much faster/better would a native 64 bit processor that wasn't backwards compatible with anything 32 bit or x86 be than the current x64 processors? I don't think such a thing even exists. Intel has IA-64, but it's a different 64 bit altogether, nothing to do with x64.

---

### Post by Frak on 2010-01-12
> **blueshiftoverwatch said:**
> Of course, that was just theoretically. In reality, since all or almost all serious new processors for desktop computing are 64 bit at this point and the clock speed and other attributes of the CPU's are getting better. The fact that it has to emulate 32 bit would probably be more than made up for by the fact that the CPU it's self is generally faster, right?

At the same clock speed, and assuming the program was just a 32-bit application compiled for both platforms, a 64-bit processor would nearly always be slower than its 32-bit counterpart. On the other hand, if an application was optimized for 64-bit, then the speeds would generally be faster, but that entirely depends on the developer and their competency.

> **blueshiftoverwatch said:**
> So, how much faster/better would a native 64 bit processor that wasn't backwards compatible with anything 32 bit or x86 be than the current x64 processors? I don't think such a thing even exists. Intel has IA-64, but it's a different 64 bit altogether, nothing to do with x64.

The only thing backwards comparability hurts is how much RAM it can support. x86_64 processors can't support the actual roof of a true ia64 processor, but at the same time, it really isn't an issue since we haven't even come close to the lower roof that the x86_64 processors have.

---

### Post by 3rdalbum on 2010-01-13
> **Frak said:**
> **Emulation**

EDIT
And there's an instruction set (like the VT extensions current processors have) that helped speed up 32-bit emulation. Some Itaniums had a 32-bit processor on-board just in case 32-bit was needed.

But why would 32-bit code exist on Itanium anyway? Compiling your code for Itanium should result in it being 64-bit, I'd think.

Or are you talking about an ia32 emulator (and/or ia32 processor on-board)?

---

### Post by NoaHall on 2010-01-13
> **3rdalbum said:**
> But why would 32-bit code exist on Itanium anyway? Compiling your code for Itanium should result in it being 64-bit, I'd think.

Or are you talking about an ia32 emulator (and/or ia32 processor on-board)?

IA-64 isn't widely supported, and nor is the source code always available.

---

### Post by ssam on 2010-01-13
these are quite technical (and slightly old), but the explain a lot of the interesting features of various CPUs
[http://arstechnica.com/cpu/index.html](http://arstechnica.com/cpu/index.html)

powerpc is not completely dead. it is still being used in games consoles, servers, supercomputers [http://en.wikipedia.org/wiki/Power_Architecture](http://en.wikipedia.org/wiki/Power_Architecture) . also the new amiga [http://www.osnews.com/story/22693/New_Amiga_Sports_Programmable_Co-Processor_Dualcore_PPC](http://www.osnews.com/story/22693/New_Amiga_Sports_Programmable_Co-Processor_Dualcore_PPC)

but cheap usually beats better, so x86 will be around for a long time.

---

### Post by del_diablo on 2010-01-13
> **NoaHall said:**
> IA-64 isn't widely supported, and nor is the source code always available.

Which got nothing to do with the question.
Itanium is 64-bit, and there does not exists 32-bit to it. So there is no 32-bit code to emulate for Intanium itself. Now, if its 90% of native x86 when emulated then it makes sense.
Or if its some really big bogus about force compiling a 32-bit app of Itanium which does not make sense.

---

### Post by cascade9 on 2010-01-13
> **Xbehave said:**
> x86_64 is 64bit x86 and is backwards compatible (requires an instruction to change to 32bit mode but, much faster x86 processing than ia64)
ia64 is 64bit not-x86 and is not backwards compatible except through emulation
X64 is a confusing term wikipedia defaults it to X86_64 but with a note for people looking for ia64

Itanium = ia64
C2D/AMD Athlon 64/Phenom = x86_64
AMD athlon= x86

+1. Technically perfect.

'X64' isnt technically an architecture. Depending on who you listen to. X64 is commonly used to mean 'x86_64' (which makes sense to me, like I've said before 'x64' implies 'x86 compatibility' IMO anyway) Even Microsoft does it-

> x64 Architecture


    The x64 architecture is a backwards-compatible extension of x86. It provides a legacy 32-bit mode, which is identical to x86, and a new 64-bit mode.
 The term "x64" includes both AMD 64 and Intel64. The instruction sets are close to identical.


[http://msdn.microsoft.com/en-us/library/cc267760.aspx](http://msdn.microsoft.com/en-us/library/cc267760.aspx)

---

### Post by DeadSuperHero on 2010-01-13
Even though PPC isn't "a contender anymore", it is still by far the best computer architechture in my opinion. It's still produced by various corporations, and for quite some time has gone to supporting Amiga hardware. So not all is lost.

It's hard to particularly explain why PPC is better. Coding for it is far more streamlined than for x86. A PPC machine with a 1.5 Ghz processor can be faster than a 2.5 Ghz x86 in some instances. I'd recommend at least taking a look into it, if not for hobbyist purposes.

---

### Post by Xbehave on 2010-01-13
> **cascade9 said:**
> Even Microsoft does it-> x64 Architecture


The x64 architecture is a backwards-compatible extension of x86. It provides a legacy 32-bit mode, which is identical to x86, and a new 64-bit mode.
The term "x64" includes both AMD 64 and Intel64. The instruction sets are close to identical. [http://msdn.microsoft.com/en-us/library/cc267760.aspx](http://msdn.microsoft.com/en-us/library/cc267760.aspx)
Just to clarify because I misunderstood, both AMD64 and Intel64 mean x86_64 (as do EM64T and IA32e)

---

### Post by Frak on 2010-01-13
> **del_diablo said:**
> Which got nothing to do with the question.
Itanium is 64-bit, and there does not exists 32-bit to it. So there is no 32-bit code to emulate for Intanium itself. Now, if its 90% of native x86 when emulated then it makes sense.
Or if its some really big bogus about force compiling a 32-bit app of Itanium which does not make sense.
90% refers to speed. It can fully emulate an x86, but the speed is only 90% native.

---

### Post by lostinxlation on 2010-01-14
> **blueshiftoverwatch said:**
>  
I'm interested in what their advantages and disadvantages are. .
 
First, x64 is an extension of 32bit x86. There isn't much to discuss if there are any advantage or disadvantage between them except address space.
 
x86/x64 is CISC which has so many instructions and addressing mode therefore it's very complicated from hardware point of view. PowerPC is RISC and RISC was originally architected to make the hardware simple and targeted faster clock frequency.
 
Major difference between RISC and CISC is
 
1. RISC has a limitted number of instructions, whereas CISC has so many.
2. GENERALLY, only load and store instructions can access memory with RISC(there are some exceptions such as a CAS or TAS instruction to run the polling on the critical sections of memory). Since CISC has so many addressing modes, even integer operations can access the memory.
3. Since RISC pursued simplicity, an instruction length is fixed. On the other hand, old CISC has instructions with variable length to work around memory shortage. This means the code size will be, in general, shorter with CISC than RISC. For the same reason, instruction decoding logic on CISC will be more compicated and messy than RISC.
4. Most of the RISC processors allows a delayed branch(an instruction in the delay slot can be executed as the branch instruction is executed. This was to avoid bubbles in the pipeline when speculative execution was not yet implemented). I doubt x86 has it if they wanted to maintain binary compatibility.
 
One of the interesting features I remember with PowerPC was it had a register that can hold the loop count in it.
 
 
To the point about what is advantage or disadvantage, you wouldn't have any if you are simply a user. These pros and cons are applicable only to those who design the microprocesors and those who write the code on assembly langurage level.

---

### Post by lostinxlation on 2010-01-14
> **blueshiftoverwatch said:**
> Aren't ARM and MIPS only suitable for lower powered handheld or embedded devices?
 
ARM and today's MIPS are targeting only low power. embedded processor market. THey aren't interested to get into high end market where x86 are already dominating. But if they jack up the clock frequency, increase the paralellism, increase the memory bandwidth within the ISA, they can go for high end market.
 
SGI used to design the high end MIPS processors and NEC also did it.
 
however, I'd guess that they cannot catch up the Intel/AMD even though they try. Simplicity of ARM/MIPS architecture allows them to have simple and fast logic, BUT having Intel/AMD that achieved over 3GHz with their highly complicated implementation, RISC camp lost their advantage. It's hard for ARM/MIPS to compete with Intel/AMD unless they can achieve 5 GHz or more because one instruction in CISC can do the job equivalent to what takes 3 or 4 instructions in RISC.

---

### Post by phrostbyte on 2010-01-17
> **lostinxlation said:**
> ARM and today's MIPS are targeting only low power. embedded processor market. THey aren't interested to get into high end market where x86 are already dominating. But if they jack up the clock frequency, increase the paralellism, increase the memory bandwidth within the ISA, they can go for high end market.
 
SGI used to design the high end MIPS processors and NEC also did it.
 
however, I'd guess that they cannot catch up the Intel/AMD even though they try. Simplicity of ARM/MIPS architecture allows them to have simple and fast logic, BUT having Intel/AMD that achieved over 3GHz with their highly complicated implementation, RISC camp lost their advantage. It's hard for ARM/MIPS to compete with Intel/AMD unless they can achieve 5 GHz or more because one instruction in CISC can do the job equivalent to what takes 3 or 4 instructions in RISC.

Well AMD/Intel's internal designs are RISC designs. They expose the x86 and x86_64 instruction sets through software that is internal to the chip, the software then translates the opcodes to the native instruction set of the processor. This has an overhead, but it's much better then trying to implement the massive mess of an instruction set they would have to do otherwise. MIPS and ARM tend to be implemented directly, ie, no microcode.

If you ignore the instruction set they expose, internally AMD/Intel chip designs are leagues ahead of anyone else (except maybe IBM), especially the control unit. That's one reason why they are so fast, the other reason is they tend to pack more electronics into the design and have access to more advanced fabrication processes. It would be sick what AMD/Intel could accomplish if they were allowed some innovation in the instruction set side of things.

---

### Post by blueshiftoverwatch on 2010-02-11
Anyone else have more information? I have to give a presentation about the shortfalls for current CPU's later this month for one of my computer classes.

I read on another forum that "*AMD's AMD64 implementation is actually 48-bit and actually tricks the computer into thinking it's 64-bit so that programs compiled for AMD64 now will still work when future processors really are 64-bit.*"

What's that about?

---

### Post by cammin on 2010-02-12
> **blueshiftoverwatch said:**
> Anyone else have more information? I have to give a presentation about the shortfalls for current CPU's later this month for one of my computer classes.

I read on another forum that "*AMD's AMD64 implementation is actually 48-bit and actually tricks the computer into thinking it's 64-bit so that programs compiled for AMD64 now will still work when future processors really are 64-bit.*"

What's that about?

AMD chips use 48 bits of virtual address space. it uses sign extension to assume the other 16 bits.


[http://www.amd.com/us-en/assets/content_type/white_papers_and_tech_docs/x86-64_overview.pdf](http://www.amd.com/us-en/assets/content_type/white_papers_and_tech_docs/x86-64_overview.pdf)
Page 48 (pdf page 54) gives you the jist of it. Plus if you like dry reading, it gives you all the  the other x86-64 features.


If you're bored and you have an AMD-64 cpu you can type
```
cat /proc/cpuinfo |grep address
```
in a terminal and see the amount of virtual and physical address space your chip supports.

---

### Post by Sporkman on 2010-02-12
> **Xbehave said:**
> PPC was/is RISC, but has droped from mainstream use since apple switched to x86 (ironically a major user is now microsoft's xbox360).

PPCs are still used a lot in embedded devices.

---

### Post by Sporkman on 2010-02-12
> **hobo14 said:**
> For example, a [MIPS supercomputer]("http://sicortex.com/products/high_capability_system_sc5832") and an [ARM supercomputer]("http://vr-zone.com/articles/nvidia-tesla-powers-29th-most-powerful-supercomputer-in-the-world/6216.html").


Awesome! 8)

---

### Post by blueshiftoverwatch on 2010-02-12
> **cammin said:**
> [http://www.amd.com/us-en/assets/content_type/white_papers_and_tech_docs/x86-64_overview.pdf](http://www.amd.com/us-en/assets/content_type/white_papers_and_tech_docs/x86-64_overview.pdf)
Page 48 (pdf page 54) gives you the jist of it. Plus if you like dry reading, it gives you all the  the other x86-64 features.
I read the first 11 pages, which were fairly interesting. After that I got to the point and was kind of lost:
```
This section describes the application register set, instruction-
set conventions, memory addressing, and application-relevant
aspects of procedure-call conventions. It is intended primarily
for experienced x86 programmers writing applications,
compilers, or assemblers. System programmers writing
privileged code should also read this section.
```
> **cammin said:**
> If you're bored and you have an AMD-64 cpu you can type
```
cat /proc/cpuinfo |grep address
```
in a terminal and see the amount of virtual and physical address space your chip supports.
48 bits physical and 48 bits virtual for each of the 4 cores.

---

### Post by blueshiftoverwatch on 2010-02-16
> **phrostbyte said:**
> Don't know about any articles. But as someone who has had to do x86 assembly language programming.. I can tell you it's a terrible, unorganized, bloated instruction set that resembles a series of tacked on hacks. ARM and MIPS are far better, and even other CISC instruction sets like 68000 are better designed.
Can you elaborate?

---

