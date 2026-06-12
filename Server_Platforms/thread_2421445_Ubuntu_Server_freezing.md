---
title: "Ubuntu Server freezing"
date: 2019-06-21
forum: Server Platforms
---

### Post by jay0 on 2019-06-21
I installed Ubuntu 16.04 on a brand new PC. The PC is completely locked up every two days and I have to power off and back on again. Below is specs of PC. IS it an issue with the  AMD Ryzen 3 2200G with Radeon Vega Graphics? Any help trying to solve this would be great.






```
System:    Host: crm Kernel: 4.4.0-151-generic x86_64 (64 bit) Console: tty 0
           Distro: Ubuntu 16.04 xenial
Machine:   System: Gigabyte product: A320M-S2H V2 v: Default string
           Mobo: Gigabyte model: A320M-S2H V2-CF v: x.x
           Bios: American Megatrends v: F1 date: 10/16/2018
CPU:       Quad core AMD Ryzen 3 2200G with Radeon Vega Graphics (-MCP-) cache: 2048 KB
           clock speeds: max: 3500 MHz 1: 1600 MHz 2: 1600 MHz 3: 1600 MHz
           4: 1600 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series]
           Display Server: N/A driver: N/A
           tty size: 80x24 Advanced Data: N/A out of X
Audio:     Card-1 Advanced Micro Devices [AMD] Device 15e3
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] Device 15de
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-151-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
```

---

### Post by TheFu on 2019-06-21
What do the system log files show?  Facts please.
Also, I thought the Ryzen CPUs with onboard GPU needed a much newer kernel to work.

Looks like a 5.x kernel is needed to get stability, but I  just have a Ryzen 2600, no onboard graphics, so I don't have any direct knowledge.  The main reason I didn't get a 'g' model was concerns over stability for 6-12 months as the kernels caught up.  I've read that 4.18 and 4.19 have random freezes.
[https://www.phoronix.com/forums/forum/linux-graphics-x-org-drivers/open-source-amd-linux/1025158-what-linux-kernel-packages-and-drivers-are-needed-for-amd-ryzen-3](https://www.phoronix.com/forums/forum/linux-graphics-x-org-drivers/open-source-amd-linux/1025158-what-linux-kernel-packages-and-drivers-are-needed-for-amd-ryzen-3) claims that 4.16 is the minimum kernel.

If you are on a supported release, then you should be able to have at least 4.15.  On my 16.04.6 systems, v4.15.0-51-generic is the kernel version.  I would try that, perhaps the Ryzen iGPU stuff got backported? IDK, but it can't hurt.  Just load the HWE stack. A guide for that [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) Be certain to go down to the instructions for your specific release.

---

### Post by houstonbofh on 2019-07-04
Can you try 18.04?  Stability issues are why I skipped 16.04 entirely.

---

### Post by SeijiSensei on 2019-07-04
Ubuntu Server is a text-mode version with no GUI. If that's what you're using, I doubt the video card would matter.

---

