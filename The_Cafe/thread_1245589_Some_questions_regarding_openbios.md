---
title: "Some questions regarding openbios"
date: 2009-08-20
forum: The Cafe
---

### Post by keiichidono on 2009-08-20
I've been interested in using an openbios for a while now and recently decided to seriously research it. I didn't know which one to choose but coreboot has a well documented and easy to understand wiki.

**Question1**: Coreboot seems to run on my architecture but it's slightly different from the GA-M57SLI-S4 it supports. By the below info, am i supported?

Processors Information
-----------------------

Processor 1			ID = 0
	Number of cores		2 (max 2)
	Number of threads	2 (max 2)
	Name			AMD Athlon 64 X2 4400+
	Codename		Brisbane
	Specification		AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
	Package 		Socket AM2 (940)
	CPUID			F.B.1
	Extended CPUID		F.6B
	Brand ID		4
	Core Stepping		BH-G1
	Technology		65 nm
	Core Speed		2310.7 MHz
	Multiplier x FSB	11.5 x 200.9 MHz
	HT Link speed		1004.7 MHz
	Stock frequency		2300 MHz
	Instructions sets	MMX (+), 3DNow! (+), SSE, SSE2, SSE3, x86-64
	L1 Data cache		2 x 64 KBytes, 2-way set associative, 64-byte line size
	L1 Instruction cache	2 x 64 KBytes, 2-way set associative, 64-byte line size
	L2 cache		2 x 512 KBytes, 16-way set associative, 64-byte line size
	FID/VID Control		yes
	Max FID			11.5x
	Max VID			1.300 V

	K8 Thermal sensor	yes
	K8 Revision ID		6.0

Chipset
-------

Northbridge			NVIDIA MCP61 rev. A3
Southbridge			NVIDIA MCP61 rev. A2

Monitoring
------------

Mainboard Model		Nettle2 (0x0000029E - 0x007EA4D2)

LPCIO
------------

LPCIO Vendor		ITE
LPCIO Vendor ID		0x90
LPCIO Chip ID		0x8726
LPCIO Revision ID	0x2
Config Mode I/O address	0x2E
Config Mode LDN		0x4

Hardware Monitors
-------------------

Hardware monitor	ITE IT87

**Question2**: Compared to the other openbios projects, is coreboot the best?

**Question3**: Is installing an alternative bios safe?

---

### Post by sydbat on 2009-08-20
I've actually been curious about this too...especially your 3rd question.

---

### Post by keiichidono on 2009-08-20
[bump]

---

### Post by keiichidono on 2009-08-21
[bump]

---

### Post by dragos240 on 2009-08-21
I wish I had an answer for any of your questions.

---

### Post by keiichidono on 2009-08-21
> **dragos240 said:**
> I wish I had an answer for any of your questions.

Me too man, me too. :(

---

### Post by lisati on 2009-08-21
> **CalvinB said:**
> **Question3**: Is installing an alternative bios safe?
I'm mildly curious as well. Part of me wants to shy away from using any BIOS other than one provided by the manufacturer even though I've encountered anecdotal evidence that some BIOS manufacturers get up to tricks like tinkering with theirs so that Windows works with it better than Linux.

---

### Post by FuturePilot on 2009-08-21
I'd like to know this as well, especially #3.

---

### Post by Frak on 2009-08-21
I want to flash the VMWare bios now... I want to see what catastrophies could occur.

---

### Post by keiichidono on 2009-08-22
[bump]

---

### Post by sydbat on 2009-08-22
I have an idea...and it might sound crazy...

If you have an old box you really don't care about, why not try and flash that bios with openbios. If it works, you should be able to determine what is better about openbios and what is not. Also, it should give you an idea of what it might do with your 'main' box. If it doesn't work, then you know th opposite.

If you do not have an old box to play with like this, maybe see if someone you know has one lying around not doing anything. I know people who buy new computers and put their old ones aside because they are not really technologically inclined and do not know what to do with the old technology.

---

### Post by BuffaloX on 2009-08-22
You could order a spare Bios for your mobo, just in case...

---

### Post by keiichidono on 2009-08-22
> **sydbat said:**
> I have an idea...and it might sound crazy...

If you have an old box you really don't care about, why not try and flash that bios with openbios. If it works, you should be able to determine what is better about openbios and what is not. Also, it should give you an idea of what it might do with your 'main' box. If it doesn't work, then you know th opposite.

If you do not have an old box to play with like this, maybe see if someone you know has one lying around not doing anything. I know people who buy new computers and put their old ones aside because they are not really technologically inclined and do not know what to do with the old technology.

Hmmm, good idea.

---

### Post by harry2006 on 2009-08-22
no coclusive response as yet!

---

### Post by Frak on 2009-08-22
> **BuffaloX said:**
> You could order a spare Bios for your mobo, just in case...
I ordered one from Biostar, just waiting for it to come in :\

---

### Post by BuffaloX on 2009-08-22
> **Frak said:**
> I ordered one from Biostar, just waiting for it to come in :\

Good call.

Also if you have two compatible motherboards, you can actually switch the BIOS after you have booted your system, and burn the original image back on the bad one. ( If all else fails and you don't have a spare. )
But I think you have to be a bit hardcore to do that.

I did it once, and it worked like a charm, but I was pretty nervous I'd short something in the process, ending up with two dead boards.

It's much better to be prepared...

---

### Post by koenn on 2009-08-22
> **CalvinB said:**
> I
**Question3**: Is installing an alternative bios safe?
I'm sure the answer to that question van be found on the websites of producers of alternative bioses, but I'm not in the mood to go look it up.

Anyway, educated guess : *using* a suitable alternative BIOS is probably save. Installing it is the tricky part, and you may end op with an unusable system. 
Also, the warranty on your PC will probably  no longer be valid when you replace the BIOS.

---

### Post by keiichidono on 2009-08-22
[bump]

---

