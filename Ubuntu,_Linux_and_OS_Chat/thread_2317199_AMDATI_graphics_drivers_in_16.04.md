---
title: "AMD/ATI graphics drivers in 16.04??"
date: 2016-03-14
forum: Ubuntu, Linux and OS Chat
---

### Post by him610 on 2016-03-14
Does anyone have any thoughts about the possibility of no AMD/ATI graphics drivers in 16.04? 
I read it in this article at omgubuntu.co.uk -
[http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04](http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04)
On the one 14.04 machine I have with a fairly recent integrated AMD APU/GPU chip, it currrently uses the fglrx driver with the alternative open-source xserver-xorg-video-ati available. 

From the article, I would think my options are: 
1. Remain on LTS 14.04 using fglrx driver
2. Upgrade to LTS 16.04 and use the xserver-xorg-video-ati??
3. Wait for release of AMD Catalyst driver based on AMDGPU then upgrade

Comments, advice, or suggestions are most welcome.

---

### Post by pauljw on 2016-03-14
Why fix what isn't broken?  If you have no other issues that require an upgrade, the best move is no move.  Stay on 14.04LTS, fully supported till 2019.

---

### Post by grahammechanical on 2016-03-14
It is in the release notes of 16.04

> The fglrx driver is now deprecated in 16.04, and we  recommend its open source alternatives (radeon and amdgpu). AMD put a  lot of work into the drivers, and we backported kernel code from Linux  4.5 to provide a better experience.


When  upgrading to Ubuntu 16.04 from a previous release, both the fglrx  driver and the xorg.conf will be removed, so that the system is set to  use either the amdgpu driver or the radeon driver (depending on the  available hardware). 



This is all explained here.

[https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/)
> 
With this move we will have the shared core of AMD’s new driver stack in  place and ready for adding the proprietary pieces of their hybrid  stack, once they have been released later this year.

My advice (apart from remaining on 14.04) would be to put in a dual boot of 16.04 to see how things run on the open source video driver. If your needs are adequately fulfilled by the open source video driver then you are good to go. But if your needs are such that only the proprietary video driver will do, then hold off and see how things develop over the coming months.

Regards.

---

### Post by mastablasta on 2016-03-14
> **hgh9mrp said:**
> 
From the article, I would think my options are: 
1. Remain on LTS 14.04 using fglrx driver
2. Upgrade to LTS 16.04 and use the xserver-xorg-video-ati??
3. Wait for release of AMD Catalyst driver based on AMDGPU then upgrade


AMDGPU will support only the most recent chips. for others there is FGLRX. if you have 14.04 then this PC is not fairly recent by AMD standards :P
In any case the issue here is that AMDGPU is not as good as fglrx and I wonder when it actually will be. some say in 6 m, some say later. hard to say. depends how well AMD will support it. I have AMD 6xxx and I have only one option - stay on LTS. radeon driver is 20-30% worse than fglrx and if I understand it AMDGPU won't support the chip anyway. so the only option is to stay on fglrx or to remove Ubuntu and just use windows (maybe updagrade to win 10 which will be supported longer than 7. 

> **grahammechanical said:**
> 
 But if your needs are such that only the proprietary video driver will do, then hold off and see how things develop over the coming months.

holding off is only any good if the chip is HD 7xxx and newer if I understand correctly. otherwise one has to deal with performance drop and possibly other issues especially on laptops (overheating, battery drains and such).

---

### Post by him610 on 2016-03-14
Thanks for all of your comments and suggestions. I remembered I had a DVD with Xubuntu 16.04 beta which I booted from. The graphics did not seem to be an issue for my purposes.

```
xubuntu@xubuntu:~$ inxi -GCS
System:    Host: xubuntu Kernel: 4.4.0-7-generic x86_64 (64 bit) Desktop: Xfce 4.12.3
           Distro: Ubuntu 16.04 xenial
CPU:       Quad core AMD Athlon 5350 APU with Radeon R3 (-MCP-) cache: 8192 KB 
           clock speeds: max: 2050 MHz 1: 1000 MHz 2: 2050 MHz 3: 1000 MHz 4: 800 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Kabini [Radeon HD 8400 / R3 Series]
           Display Server: X.Org 1.17.3 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1680x1050@59.95hz
           GLX Renderer: Gallium 0.4 on AMD KABINI (DRM 2.43.0, LLVM 3.8.0)
           GLX Version: 3.0 Mesa 11.1.2

```

---

### Post by ales on 2016-06-14
What does it mean - only most recent chips. I have AMD 270X Curacao XT and their beta driver starts with support from R285. Does it mean also my chip will not be supported? So for me nVidia would be a  way to go? One thing which I noticed after upgrading to 16.04, (using Gnome Shell) the system is much smoother with radeon driver than it was with fglrx under previous ubuntu version. But no Steam or decent gaming is possible.

---

### Post by QIII on 2016-06-14
With regard to the AMDGPU driver, "latest chips" means the GCN (Graphics Core Next) 1.2 compatible chips -- which are at present the Volcanic Islands chipsets:  Tonga and Fiji.  The model numbers of the AMD GPUs are not necessarily indicative, but some included adapters are the R9 285, R9 Fury, R9 380X.  The R9 290X and R9 390X are not included, nor are many of the R7 adapters and below.  There is current experimental support for some GCN 1.1 cards (expected to be completed by August) and we may even see support for GCN 1.0 cards.  AMDGPU will also support/be supported by some of the new products (Arctic Islands, Polaris GCN 1.3) coming out at the end of this month or early July.

(For a breakdown of GCN by GPU, there is a good bit of information [here]("https://en.wikipedia.org/wiki/List_of_AMD_graphics_processing_units").  You'll want to start by scrolling down to "Radeon HD 8xxx Series".  You'll see that your Curacao is GCN 1.0.)

AMDGPU works better than fglrx on my R9 380X and better than fglrx did on my R9 290X. It may take Steam some time to catch up, however.

fglrx was not included in 16.04 because Canonical pressed forward with a new version of X Server that fglrx was not ready to handle and AMD did not want to expend the resources to make it compatible while they are working so hard on AMDGPU and AMDGPU-Pro.

Based on some statements from both Canonical and AMD, it is widely rumored that fglrx will reappear in 16.04.1.  I hope that will happen.

This period of turmoil is caused by the fact that AMD is finally doing what we have been asking for it to do for years:  create a truly useful and feature-rich open source driver.  That is now the AMDGPU driver.  In the new scheme, the proprietary driver, AMDGPU Pro, is based on the open source driver.  That's a pretty nice job of turning the old way of doing things on its head.  And we will also have a much improved Radeon driver to boot.

Is NVIDIA better for you?  Only you can make that choice.  But understand that this bit of craziness is temporary and should result in a profound positive change in AMD support for Linux.

But for right now, it's crazy.

---

### Post by yoshii on 2016-06-14
QIII, you really know a lot about this topic.  I'm thankful to you for explaining this stuff.  It's hard to find this info elsewhere.

---

### Post by entw on 2016-09-05
I can only add here that on my GCN 1.1 card radeon driver is the only option so far. AMDGPU driver doesn't work, but it was working before. Somehow they've dropped support of it.

---

### Post by QIII on 2016-09-05
Somehow who has dropped support?

AMD still supports it.  The kernel still includes the module.

---

### Post by 6975 on 2016-09-07
Let me tell you something even you've fglrx it'll slow down your window dragging.
I've already test fglrx on both Debian 8.0 with fglrx-driver+fglrx+control
and ubuntu with fglrx-installer there's no difference.

If you're still persistent to get it just run 15.10 & you've get latest stuffs as 16.04 & got support for fglrx as 14.04
Since Ubuntu 14.04 use xorg 1.16 while 15.10 got 1.17 fglrx is fully support.
If you're on Ubuntu 16.04 xorg is 1.18 which will never support fglrx driver.
That's also applied to all other Linux distro that use xorg 1.18 re unable to run any fglrx driver.

Unless you get it from here which is still beta for 16.04
[http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx)

---

### Post by mastablasta on 2016-09-07
> **6975 said:**
> 

If you're still persistent to get it just run 15.10 & you've get latest stuffs as 16.04 & got support for fglrx as 14.04

wrong - you do not get the latest "stuffs" as it is no longer supported. so the only option is 14.04 and maybe 14.04.1. or live with radeon driver and hope it will imrpove in time.

---

### Post by 6975 on 2016-09-08
> **mastablasta said:**
> wrong - you do not get the latest "stuffs" as it is no longer supported. so the only option is 14.04 and maybe 14.04.1. or live with radeon driver and hope it will imrpove in time.

Then this is devil proof, then?
[https://launchpad.net/ubuntu/wily/+source/fglrx-installer](https://launchpad.net/ubuntu/wily/+source/fglrx-installer)
[https://launchpad.net/ubuntu/+source/fglrx-installer](https://launchpad.net/ubuntu/+source/fglrx-installer)

I used to think same as you do that there're no any other fglrx driver for 15.10 than just 14.04-14.04.1
but now this devil proof broke your & mine old believe into bits.
Also the other latest softwares I can just get it from any PPA on launchpad.net or from any official website of that softwares.
For example Uget:
[http://ugetdm.com/downloads-ubuntu](http://ugetdm.com/downloads-ubuntu)
[https://launchpad.net/~plushuang-tw/+archive/ubuntu/uget-stable](https://launchpad.net/~plushuang-tw/+archive/ubuntu/uget-stable)

---

### Post by mastablasta on 2016-09-08
> **6975 said:**
> Then this is devil proof, then?
I used to think same as you do that there're no any other fglrx driver for 15.10 than just 14.04-14.04.1
but now this devil proof broke your & mine old believe into bits.
Also the other latest softwares I can just get it from any PPA on launchpad.net or from any official website of that softwares.


nope. kernel is not patched neither is other software that makes the OS and and various "services" and libraries. You can ofcourse use it but the release is EOL, which means if someone hacks you because you used unpatched stuff, then the fault would be entirely yours.

on the other hand 14.04 is supported until 2019 and if you need newer software - like you said you can use PPA.

since setting up server and a few services - the attacks are daily. so yes, there is a risk, eventhough there is no known virus in the wild. but one can still get in through borwser, infected site, java script... which is why we advise users to use a supported version of the OS rather than encourage them to use an unsafe version. 

if it really has to be 15.10, then i would dualboot an duse 15.10 only for gaming for example.

if you use old and unsupported OS you better know what you are doing. i still use windows XP on one machine. it has plenty of 3rd party protections i added. still i am afraid of possible breach. various ports were closed down, backups are made, webbrowsers have various no script and such addons...

---

### Post by 6975 on 2016-09-08
> **mastablasta said:**
> nope. _kernel is not patched neither is other software that makes the OS and and various "services" and libraries. You can ofcourse use it but the release is EOL, which means if someone hacks you because you used unpatched stuff, then the fault would be entirely yours._

on the other hand 14.04 is supported until 2019 and if you need newer software - like you said you can use PPA.

since setting up server and a few services - the attacks are daily. so yes, there is a risk, eventhough there is no known virus in the wild. but one can still get in through borwser, infected site, java script... which is why we advise users to use a supported version of the OS rather than encourage them to use an unsafe version. 

if it really has to be 15.10, then i would dualboot an duse 15.10 only for gaming for example.

if you use old and unsupported OS you better know what you are doing. i still use windows XP on one machine. it has plenty of 3rd party protections i added. still i am afraid of possible breach. various ports were closed down, backups are made, webbrowsers have various no script and such addons...
:-kOkay, I'll acknowledge _this proper reasoning._
If 15.10 really lack of that kernel modules.  If you're against about staying with 15.10 channel
because it's not lts I'd get your point what you mean.

I just gave OP an extra choice as the last resort. Because 16.04 they've clone channel repo from 15.10 but without fglrx driver for 16.04
I've notice that xorg 1.17 still work with fglrx. In fact I don't agree about stay on proprietary drivers. 
I'd rather stay with xorg. Even Debian Jessie only have fglrx-drivers as 14.04-15.10
I'm also an AMD gamer here that survive without using AMD proprietary currently.

AMD have been focus too much about make Zen Core CPU that cause a large delay of update GPU driver for xorg 1.18+

---

