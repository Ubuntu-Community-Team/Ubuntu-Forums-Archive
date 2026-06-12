---
title: "What luck in general with older system hardwares?"
date: 2016-03-05
forum: Ubuntu, Linux and OS Chat
---

### Post by bcschmerker on 2016-03-05
As of 4 March 2016 I am acquiring upgrade hardware for the Hot Rod gPC™ (Advanced Micro Devices® Athlon 64® X2 5600+, RS780G/SB710 chipset) in preparation of a major Dist-Upgrade to Ubuntu® 16.02b1, 16.03b2, or 16.04rc Xenial Xerus™ (target RTM for 16.04.0-LTS: 25 April 2016).  To replace the aging Seagate® master and Fujitsu® slave E-IDE drives in the system since 2008, I have acquired two of three planned Toshiba® PH2050U-1I54 2.5" hard disc drives, and - due to a shortage of SATA power ports on the Antec® TruePower® New™ 750 Blue's built-in harness and the loss of the auxiliary SATA harness during the move to Byron from Bethel Island - a Western Digital® WD1600JS-55MC01 3.5" hard disc drive that happens to be a transitional unit (it packs a 4-pin Molex jack compatible with splitters available at Fry's Electronics and other shops).  A "backgrade" E-IDE DVD Super Multi optical drive (manufactured for an OEM by Toshiba Hitachi) is now installed and already wired for power, pending the hard-drive shuffle.  Given the interim SATA DVD super multi's perfect track record (in IDE mode) on Port SATA2-4 on the Gigabyte® GA-MA78GM-S2HP Rev. 2.0, I anticipate no critical problems for the triple PH2050U's and WD1600JS between Ports SATA2-0 through SATA2-3 (in AHCI mode).  The TP750 has two 6+2-pin PCIe auxiliary power harnesses available for video upgrade; but I can see only upgrading to a Gigabyte® GV-R577D5-1GD-B (850 MHz Advanced Micro Devices® RV870 Pro GPU; 1 GiB 128-bit GDDR5-4800 video memory), given the SNAFU I faced attempting to integrate an Asus® EAH6850DC/2DIS/1GD5/V2 (790 MHz Advanced Micro Devices® RV970 Pro GPU, 1 GiB 256-bit GDDR5-4000 video memory) into a mobo originally manufactured when 256-bit video cards hadn't been introduced to market.  Maybe an upgrade to BIOS F5 or F6D can address this problem and allow the Gigabyte® GV-R695D5-2GD-B (800 MHz Advanced Micro Devices® RV990 Pro GPU, 2 GiB 256-bit GDDR5-5000 video memory) to work properly....

How has the Ubuntu® experience been in general for rebuilders able to take advantage of recently-discontinued SATA2 drives with either planar ports or PCI/e RAID host controllers, and related hardwares such as video, USB 3.*n* I/O, &c. to update older motherboards and upgrade power supplies?

---

### Post by sudodus on 2016-03-05
I have not really rebuilt any computer (only exchanged some components), but I have a computer with a similar Athlon (slightly weaker: 'AMD Athlon(tm) 64 X2 Dual Core Processor 4400+', mounted on an ASUS 'M2N-VM DVI' motherboard. I have been iso-testing Lubuntu Xenial (to be released as 16.04 LTS), and it works well with that hardware. Lubuntu Xenial works in older computers too, I have tested in an old Dell Dimension 4600 with a Pentium 4 CPU and in an old IBM Thinkpad T42 with Pentium M, where it works too.

---

### Post by grahammechanical on 2016-03-05
Leaving aside, the, no doubt, interesting subject of bringing old motherboards into the new century, the components that matter when it comes to installing Linux are CPU, amount of RAM & GPU + amount of its own video memory.

 The GPU and the amount of memory it has is important because the more work that the GPU does the less for the CPU & RAM = better user experience. Besides there are some Linux distributions that require a GPU that can do hardware accelerated 3D rendering. Ubuntu with Unity is one of those distributions. Ubuntu family distributions that do not have this requirement are Xubuntu, Lubuntu & Ubuntu Mate.

The latest versions of the Ubuntu family will have the latest proprietary video drivers but the latest proprietary video drivers will have dropped support for older video adapters. That is something to watch out for.

Regards.

---

### Post by him610 on 2016-03-06
I have a Shuttle XPC SN68 with the same Athlon 64® X2 5600+ CPU along with 4GB RAM, Nvidia 8500 GT, Samsung 840 250GB SSD, Rosewill RNX N300 (RT2760) wireless card, and Logitech K400r keyboard & M325 wireless mouse. I acquired it new about 8 years ago, stripped it for components a couple of years ago. I was considering scrapping it, but decided to rebuild it instead. It has Ubuntu 14.04.4. It is one of my more stable machines.

---

### Post by bcschmerker on 2016-03-06
**Congrats on the successful Shuttle® rebuild.**  One problem upgrade I see at OMS Japanese Christian Church in terms of existing computers on site is a Dell® OptiPlex&#8482; 740 desktop (Half-height micro-BTX w/ 275W PSU; 2.7 GHz? Advanced Micro Devices® Athlon64® Business Class&#8482;, exact submodel unknown (Socket AM2); nVIDIA® NVS 210S NB/nForce® 430 SB), a known temperamental combination that often demands NoModeSet at the GRUB level; I haven't planned on additional new hardware beyond upgrading system main memory to 8 GiB DDR2-800, fitting ideally dual 2.5" Toshiba® PH2100U-1I54 hard drives, and retrofitting a Mitsumi® FA404 disquette drive/CF-MD-SD-MS card interface due to lack of space for an upgrade PSU.  The implementation of XUbuntu® 16.04.0-LTS (to replace the original Microsoft® Windows® 5.2 installation) is contingent on fixes in X11R9 Nouveau for the Curie microarchitecture of nVIDIA® C60-series GPU's.

---

### Post by Bucky Ball on 2016-03-07
@bcschmerker: Please start using reasonable sized paragraphs. Black blob 'Walls of text' decrease your chances of a response and are not encouraged here. Thanks and good luck.

Dragged a heap of old machines from their hospital beds using Xubuntu or a minimal install over the last eight years.

---

