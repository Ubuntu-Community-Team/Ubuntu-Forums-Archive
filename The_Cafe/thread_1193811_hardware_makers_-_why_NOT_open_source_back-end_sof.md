---
title: "hardware makers - why NOT open source back-end software, drivers, etc?"
date: 2009-06-21
forum: The Cafe
---

### Post by earthpigg on 2009-06-21
what reasons are there for hardware vendors NOT to open-source their drivers? 

-Trademark law will allow HP, for example, to be the only ones to claim a given software driver is "Official and supported" for a given Printer. 

-Make it clear to end-users that using unofficial drivers, compiling from source, etc, voids the warranty on the hardware (if you want). 

-If the open source community manages to improve software supporting a given piece of hardware and give it additional capabilities, NVIDIA or HP or whomever can go ahead and integrate it into their "official" software, if they so choose, thus making their product (graphics card, printer, etc) that much better, and making customers that much happier. 

-possibly shifting the burden of hardware support from hardware makers to operating system vendors, except in the case of brand-spanking-new hardware. (linux already supports more hardware than windows or OS X - if your printer driver comes from an install CD or the hardware maker's website, that means the hardware vendor is supporting the hardware, not windows or OS X. this shift will help windows and mac users out, too.) 

-the last point will result in happier customers. perhaps plug n play will give you 90% of the capabilities of your hardware (wireless modem, whatever), with that last measure of perfect performance coming from the install cd or website download. 

possible cons - 

-conceivable, i suppose, that ATI could use source code for NVIDIA cards to improve their own video cards. could be illegal, and not likely to be practical anyways, but conceivable. 

-GPLv3 would prevent "TiVo-isation" or however they spell that. solution: dont use GPLv3. when you already have an existing closed-source product and you want to open source it, you can pick and choose an exact license that suits your needs exactly. 

-3rd parties selling 'improved' software to go with your hardware. solution: see above about a custom license. or just get over it and use the GPL -- you aren't selling software anyways, you are selling hardware... if someone else wants to make money by making your hardware work better, that is no money out of your pocket. again, hardware maker's choice.

---

### Post by CJ Master on 2009-06-22
> **earthpigg said:**
> 
-conceivable, i suppose, that ATI could use source code for NVIDIA cards to improve their own video cards. could be illegal, and not likely to be practical anyways, but conceivable. 


No, actually, that's the reason.

---

### Post by earthpigg on 2009-06-22
> **CJ Master said:**
> No, actually, that's the reason.

are ATI and NVIDIA cards *that* similar?

i always assumed they where not, hence the difference in how easy it is to get an NVIDIA card to work with linux compared to an ATI card....

---

### Post by Aearenda on 2009-06-22
It doesn't matter how similar they are - it's the clues in the code as to how the hardware works, or what flaws or weaknesses it might have, that matter. Anything to gain or keep a competitive advantage counts in the commercial world.

---

### Post by T.J. on 2009-06-22
Why not?  The reasons I've ever heard are something like this:  

1) Because hardware some makers license microcode and patented material from others for their products.  They are under legal obligation NOT to release the materials.  As far as I've heard, NVidia has this problem.  They would like to release an open driver, but cannot disclose certain data because of licensing agreements. 

2) Because they are afraid that they will not be able to recover their costs. Some won't take the risk because they feel they have obligations that may not be met with open sourcing.  

3) Because mindsets are slow to change.  Opensource is young, compared to corporate culture.

---

