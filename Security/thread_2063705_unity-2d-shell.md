---
title: "unity-2d-shell"
date: 2012-09-27
forum: Security
---

### Post by mike acker on 2012-09-27
[SIZE=2]what is[/SIZE][SIZE=2] unity-2d-shell ??

i found it running on my nix box this morning but i don't remember starting it.

i googled it and it seems to be just part of automatic updates for 12.04 Ubuntu

please forgive me if i'm asking a dumb question i'm still a total n00b on Linux

( but the parts for my new U-box started to arrive today.  I have the case, power supply, and motherboard.  planning to use the 4core 3.4 ghz Phenom II cpu  ) .
[/SIZE]

---

### Post by cariboo on 2012-09-28
Unity-2d is the fallback mode for systems that don't have enough resources to run Unity-3d. If you don't have a supported graphics card, Unity will automagically fallback to 2d mode. Nothing to worry about.

**Note:** In Quantal (12.10) Unity-2d is no longer available, and instead, if your system doesn't have enough resources to run Unity in 3d mode, llvmpipe is used, which uses the CPU instead of the GPU to do graphics rendering.

---

### Post by mike acker on 2012-09-28
> **cariboo907 said:**
> Unity-2d is the fallback mode for systems that don't have enough resources to run Unity-3d. If you don't have a supported graphics card, Unity will automagically fallback to 2d mode. Nothing to worry about.

**Note:** In Quantal (12.10) Unity-2d is no longer available, and instead, if your system doesn't have enough resources to run Unity in 3d mode, llvmpipe is used, which uses the CPU instead of the GPU to do graphics rendering.
~~
that would be the case then: my U-Box is an old Dell/Dimension that the kids brought back to me... it has XP on it + so many infections it couldn't even run

I reformatted both disks and installed Ubuntu 12.04 LTS on it -- which runs pretty good -- surprisingly for a single core 2.4 ghz cpu w/ 1GB ram.  the performance monitor shows the cpu 100% loaded anytime i'm doing much of anything ...

kinda of expected, but hey!! it has provided a path for me to learn Ubuntu.  I'm currently building me a real hog to run Ubuntu on to take over as my main computer.   IMHO Windows is beyond salvage.  I will not be surprised to see Canonical/Ubuntu become the preferred commercial workstation -- sooner than folks might expect.

I'm not a gamer so I am not planning to put a graphics card in my new U-Box; rather I've selected a mobo w/integrated graphics

---

