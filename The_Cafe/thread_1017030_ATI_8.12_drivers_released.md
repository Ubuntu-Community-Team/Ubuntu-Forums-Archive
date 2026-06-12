---
title: "ATI 8.12 drivers released"
date: 2008-12-20
forum: The Cafe
---

### Post by Zero Prime on 2008-12-20
The new ATI drivers are out.  Thanks to this release I can finally use hybrid crossfire in Linux!
> The addition in Catalyst 8.12 for Linux is support for Hybrid CrossFire with the RS780 Chipset. Catalyst 8.8 had introduced Linux CrossFire support to split the rendering workload between two discrete GPUs, but now it's possible to use Hybrid CrossFire on Linux, which allows the rendering workload to be split between a supported ATI integrated graphics processor and a supported PCI-E discrete graphics card.

Catalyst 8.12 also adds support for reading the bus bandwidth and memory bandwidth from the AMD Catalyst Control Center for Linux Edition (AMDCCCLE). AMD's Stream Computing is also now supported from the mainline Linux driver. There is, however, no OpenCL Linux support quite yet.

The Catalyst 8.12 driver also officially supports Ubuntu 8.10. Packaging scripts for SuSE and Mandriva have also been updated. A few random fixes have also worked their way into this release.

To much dismay, Advanced Micro Devices will not be introducing their new Linux video API, X-Video Bitstream Acceleration, in this release. The XvBA and XvMC libraries are still shipping with the driver, but the XvBA support is no good without patches that add support to media players for this API or until AMD provides the needed documentation.

---

### Post by Mazza558 on 2008-12-20
Is it any faster than the one that came with Ibex?

---

### Post by Zero Prime on 2008-12-20
For me it's a lot better and a little faster.  I don't get that full screen video/OpenGL bug any more that a lot of people were getting.

---

### Post by giantoz on 2008-12-20
How do I install?

---

### Post by handy on 2008-12-20
I've been using Catalyst 8.53 on Arch for about 3 or 4 days, which is a vast improvement on the buggy previous (3 day older) version, for me at least, others still have serious problems with 8.53 too.

I think, (though I could be wrong) that they could be tied to the new version of x.server that came out on the same day as the pre 8.53 version of Catalyst that caused problems.

Of course that x.server is troublesome to many also, many of us have to turn all of its new changes off to be able to use our keyboard & mouse.

Living with Ubuntu, you miss out on all the fun of the bugs at the cutting edge. :-)

That's not to say that Arch has to deal with many, but in October there was a kernel bug, & just now there is the xserver & Catalyst bugs.  That is all I've had to deal with in 8 months or so of Arch use. :-)

***[Edit:]** After writing the above, I thought I'd do my usual daily total Arch system upgrade; so in the Terminal I typed in yaur, which is my alias for yaourt -Syu --aur , after the quick synch of my machine with the server database I saw that xorg.server has been upgraded to version 1.5.3-4 , I wonder what effects the installation of this version will have? :-) *

---

### Post by Zero Prime on 2008-12-21
> **giantoz said:**
> How do I install?
All I did was download the installer, right click on it and go to Properties and then click the permissions tab.  Under the permissions tab I clicked on allow executing as program.  I then opened terminal and typed 

sudo (name of installer goes here) and then enter
Or you can type sudo and drag and drop the installer into the terminal.  After doing that you must delete the quotations from around the installer name.  Then press enter and follow the instructions.

---

### Post by MaxIBoy on 2008-12-21
> The addition in Catalyst 8.12 for Linux is support for Hybrid CrossFire with the RS780 Chipset. Catalyst 8.8 had introduced Linux CrossFire support to split the rendering workload between two discrete GPUs, but now it's possible to use Hybrid CrossFire on Linux, which allows the rendering workload to be split between a supported ATI integrated graphics processor and a supported PCI-E discrete graphics card. I've been waiting for this. Hopefully, it will have the good sense to split the work 80/20 instead of having my 1066 Mhz DDR2 drag down the VRAM to its level.

---

### Post by slicemaster on 2009-01-04
I saw that these drivers were released as well but am currently concerned with going through the effort of installing them if the don’t fix my video problems in XBMC. I have never had any issue with nvidia drivers under ubuntu but ATI has been nothing but a nightmare for me as it has some weird bug that screws up video playback in XBMC, ironically the same bug was also present in the Windows version of the drivers as well until those were fixed recently. Anyways, what ATI drivers are installed when you use Ubuntu’s closed-source driver installer? I am currently running those and I still have issues with XBMC so I was wondering if the drivers ubuntu provides are old. Anyways, how can I check what version of the drivers ubuntu has installed, and how can I easily install the most recent version if ubuntu is using an out of date driver.

Thanks,
Slice

P.S. and can anyone tell me is XBMC is working correctly with these new drivers?

---

