---
title: "Canonical porting Ubuntu to the ARMv7 platform, will be launced on new netbooks"
date: 2008-11-13
forum: The Cafe
---

### Post by billgoldberg on 2008-11-13
I don't know if this has been posted yet, and the link is translated by google from dutch (not so good), but still, this is good news.

[http://translate.google.com/translate?u=http%3A%2F%2Ftweakers.net%2Fnieuws%2F56733%2Fcanonical-maakt-ubuntu-port-voor-armv7-netbooks.html&hl=en&ie=UTF-8&sl=nl&tl=en](http://translate.google.com/translate?u=http%3A%2F%2Ftweakers.net%2Fnieuws%2F56733%2Fcanonical-maakt-ubuntu-port-voor-armv7-netbooks.html&hl=en&ie=UTF-8&sl=nl&tl=en)

---

### Post by I-75 on 2008-11-13
> **billgoldberg said:**
> I don't know if this has been posted yet, and the link is translated by google from dutch (not so good), but still, this is good news.

[http://translate.google.com/translate?u=http%3A%2F%2Ftweakers.net%2Fnieuws%2F56733%2Fcanonical-maakt-ubuntu-port-voor-armv7-netbooks.html&hl=en&ie=UTF-8&sl=nl&tl=en](http://translate.google.com/translate?u=http%3A%2F%2Ftweakers.net%2Fnieuws%2F56733%2Fcanonical-maakt-ubuntu-port-voor-armv7-netbooks.html&hl=en&ie=UTF-8&sl=nl&tl=en)



[http://www.linuxdevices.com/news/NS9527593286.html](http://www.linuxdevices.com/news/NS9527593286.html)


Canonical announced it will port Ubuntu Desktop Linux to the ARMv7 architecture. Targeted at netbooks, the Ubuntu ARM distribution could set the stage for Intel to lose the "software advantage" that has enabled x86 to shrug off attacks from other architectures for the last 30 years.

Cellphone giant Nokia has long sponsored an unofficial project to port Ubuntu to ARM. Now, though, new ARM capabilities in the Linux kernel such as highmem support should make it possible to compile ALL of Ubuntu on ARM, including OpenOffice and Java. Especially now that both Canonical and ARM, Ltd. have gotten involved.

Compared to X86, ARM has always had a power advantage, especially in terms of the power used when idle. An ARM-based device such as Nokia's N810 Internet tablet can last several weeks in standby mode, with a cellphone-sized battery, while early devices based on Intel's most power-efficient Z5xx-series Atom processors are lasting typically less than six hours.

On the other hand, the "Intel Architecture" as Intel now styles x86 has a 30 year history of winning in the market thanks to the existence of so much x86 software. Software dominance enabled x86 to withstand many attacks from more elegant architectures through the years -- DEC's Alpha, IBM/Apple/Motorola's PowerPC, Sun's SPARC, HP's PA-RISC, and so on.

Yet, with Ubuntu poised to bring practically the whole world of open source software to ARM, a tectonic shift away from x86 could well be underway.

---

### Post by billgoldberg on 2008-11-13
Thats a better one :p.

I would love to see ARMv7 become the standard, judging on the power it uses compared to Intel platform.

---

### Post by Changturkey on 2008-11-13
Any idea when these ARM netbooks will be out? Only thing I know of is the Pandora.

---

### Post by p_quarles on 2008-11-13
> **billgoldberg said:**
> Thats a better one :p.

I would love to see ARMv7 become the standard, judging on the power it uses compared to Intel platform.
My understanding is that they are seriously lacking in the kind of heavy-lifting power that Intel chips have. Yes, standby power savings are much better, but at the cost of very limited instruction sets. 

It also bears saying that Debian has been releasing an ARM version for years, so this isn't really groundbreaking.

---

### Post by handy on 2008-11-13
It is good news indeed.

Though from what I have read in the Whirlpool forums, it would seem that many people who buy netbooks find after a few weeks or so that they don't really use them.  I wonder if netbooks are really a fad that will eventually find a much smaller niche market?

---

### Post by Frak on 2008-11-13
Why not PowerPC, and why have they stopped supporting PowerPC.

Listen to me when I say this will be a failed experiment (yes, I said experiment).

---

### Post by phrostbyte on 2008-11-13
> **p_quarles said:**
> My understanding is that they are seriously lacking in the kind of heavy-lifting power that Intel chips have. Yes, standby power savings are much better, but at the cost of very limited instruction sets. 

It also bears saying that Debian has been releasing an ARM version for years, so this isn't really groundbreaking.

ARM is a much better instruction set then x86. In fact that's not saying much, because x86 is a terrible, unholy mess of an instruction set, that should die in a fire. And yes I say this as a person who had to program in x86 assembly. The only reason Intel themselves haven't dropped it yet is because of the amazing dependence of x86 by Windows and Windows apps. It pains me to see such powerful hardware like the Intel CPUs being driven by an extremely complex microarchitecture dominated by a mess of instructions. Really once/if Linux takes off you will see a lot innovation and diversity with instruction sets. One unique power of open source software, is the simplicity where decisions like this one can be accomplished.

---

### Post by solitaire on 2008-11-13
The Articles i've seen say you'll start seeing ARM based NetBooks pop up on the market around the middle of '09.

They will probably try and get these on the market ASAP due to Microsoft's work on Windows7. Microsoft are planning to make a version of Windows7 run on Atom CPU's as a direct competitor to their XP and our Ubuntu based NetBooks.

Note the reason people are excited by this new ARM chip is the fact that on a like for like basis the ARM chips are better suited to low-power - high efficiency devices. The Nokia N810 internet tablet can stay on standby for weeks while a similar Atom CPU can last less than 6 hours. (although the x86 architecture is more robust and well established)

The increased power supplied by a Laptop batters in the new notebooks can make it easy to imaging that an ARM Netbook could last over the 24 hours mark for usage and well over a week on standby. Having a single device that you can use all day and not need to stop every few hours to recharge or replace battery will be a huge benefit.

---

### Post by zmjjmz on 2008-11-13
> **solitaire said:**
> The Articles i've seen say you'll start seeing ARM based NetBooks pop up on the market around the middle of '09.

They will probably try and get these on the market ASAP due to Microsoft's work on Windows7. Microsoft are planning to make a version of Windows7 run on Atom CPU's as a direct competitor to their XP and our Ubuntu based NetBooks.

If the ARM CPUs are popular enough, perhaps MS will port Windows 7 to the ARM architecture?

---

### Post by solitaire on 2008-11-13
> **zmjjmz said:**
> If the ARM CPUs are popular enough, perhaps MS will port Windows 7 to the ARM architecture?

Windows CE / Mobile devices run on ARM Devices (I got an old Compaq Pocket PC that's got an ARM CPU and it ran Windows CE, but i wiped it's flash and stuck linux on it:D )

They may port Win7 to ARM but it depends, that have a lot invested in getting Win7 right first time so they may play it safe and just have a x86 version.

---

### Post by zmjjmz on 2008-11-13
> **solitaire said:**
> Windows CE / Mobile devices run on ARM Devices (I got an old Compaq Pocket PC that's got an ARM CPU and it ran Windows CE, but i wiped it's flash and stuck linux on it:D )

They may port Win7 to ARM but it depends, that have a lot invested in getting Win7 right first time so they may play it safe and just have a x86 version.

Last I heard WinCE is crap, and WinMo is too and also will not be suitable to this kind of platform.

---

### Post by solitaire on 2008-11-13
WinCE and Mobile are the only Microsoft OS's that run on ARM based devices. They were functional at best and dam annoying when trying to get suitable applications!

The only Hope Microsoft have in winning the "NetBook" war is to either recompile and Repackage a version of XP as an ARM Netbook OS or port a version of Win7 to ARM as well as Atom.

---

### Post by zmjjmz on 2008-11-13
Well supposedly Win7 already runs nicely on Atom netbooks, but yeah they'll need some ARM things going for it.

Either that or they'll have to do a major revamp of WinCE.

---

### Post by Frak on 2008-11-14
> **zmjjmz said:**
> If the ARM CPUs are popular enough, perhaps MS will port Windows 7 to the ARM architecture?
Nah, they'll just improve Windows CE, as it already runs on the ARM (RISC) processor. It also supports PowerPC, EHEM.

---

### Post by kernelhaxor on 2008-11-14
how does the ARM cpu compare with Intel Atom in terms of performance?
anyone hav benchmarks or something?

---

### Post by Frak on 2008-11-14
> **kernelhaxor said:**
> how does the ARM cpu compare with Intel Atom in terms of performance?
anyone hav benchmarks or something?
You cannot compare a RISC and a CISC. The CISC philosophy is many, complex instructions (SSE4), higher clock rates while the RISC philosophy is modest clock rates (stable), simple shorter instructions (AltiVec).

---

