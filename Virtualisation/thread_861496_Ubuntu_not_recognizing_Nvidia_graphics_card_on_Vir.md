---
title: "Ubuntu not recognizing Nvidia graphics card on VirtualBox, 800x600"
date: 2008-07-16
forum: Virtualisation
---

### Post by philip_doherty on 2008-07-16
Hi,

I've recently installed Ubuntu (Hardy Heron, 8.04) on VirtualBox on two of my dell laptops (D430,1720) and I can not get the screen resolution to change from 800x600 on either of them.

The Dell 1720 is running Vista Business and the D430 is running Windows XP Home.

The Dell 1720 has an Nvidia 8600 in it and the D430 has an intel mobile chipset. I've gone to the hardware driver section but theres is nothing listed there so I can't enable anything. I've tried downloading the drivers manually but as a complete newbie I cant be sure I've installed it correctly.

I've also tried installing various packages but nothing seems to work.

When I reboot the machine now it tells me its running in low graphics mode and I can go in and pick the nvidia driver but it doesnt accept it, its driving me nuts becuase I want to use it but an 800x600 screen is unusable.

The last thing I tried was installing the latest version of envy but it doesn't detect the NVidia card. Is there an equivalent to device manager in ubuntu?

---

### Post by Masoris on 2008-07-17
Hardware on VirtualBox is NOT real hardware, all of them are emulated one. That means you cannot use real hardware on virtulbox, you should use emulated hardware. Install VirtualBox guest tools to install drivers.

If you cannot escape form 800x600 screen resolution after installing guest tools, it could be a bug: [http://www.virtualbox.org/ticket/1689](http://www.virtualbox.org/ticket/1689)

---

### Post by philip_doherty on 2008-07-18
Yea,

I tried everything to get it working but VirtualBox can not access the video card, it doesnt look like a bug its just not a feature of virtualbox, big limitation in my view. 


My only solution was to dual boot my system. It recognised the Nvidia card and it was easy to set up.

Does anyone know if a Wubi install can access the video card and if its as fast as a virtual (or faster?).

---

### Post by l4_gerardo on 2008-09-27
Has anyone tried to install "Analize3d" or "BeOS 5" on a VM, i wonder if that could work.

---

### Post by gjoellee on 2008-09-27
Well running an xfix should solve the problem. Read how: [http://www.kshoster.net/node/18](http://www.kshoster.net/node/18)

---

