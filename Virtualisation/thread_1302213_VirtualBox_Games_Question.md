---
title: "VirtualBox: Games Question"
date: 2009-10-26
forum: Virtualisation
---

### Post by slyrDVS on 2009-10-26
If run a virtualization of WinXP 64x with a copy of the latest VirtualBox (64x for Ubuntu/Linux) what will be the quality of the games that I play, such as The Orange Box, L4D, Crysis, and Battlefield 2?

My system specs are:
Amd Phenom 9950 Quad-Core 2.61GHz
4.00 Gig of ram
ATI Radeon HD 3800 Series Video Card

---

### Post by shaggy999 on 2009-10-27
You probably won't be able to run any of those games in VirtualBox. Virtualbox emulates a PC along with all the components, including the graphics card and emulating 3D stuff is tricky at best. There is experimental support for some 3D stuff depending on the situation (I think it only supports OpenGL and not DirectX/3D) in the latest version of Virtualbox (3.0+), but it works by interfacing with WINE as a wrapper.

---

### Post by slyrDVS on 2009-10-27
> **shaggy999 said:**
> You probably won't be able to run any of those games in VirtualBox. Virtualbox emulates a PC along with all the components, including the graphics card and emulating 3D stuff is tricky at best. There is experimental support for some 3D stuff depending on the situation (I think it only supports OpenGL and not DirectX/3D) in the latest version of Virtualbox (3.0+), but it works by interfacing with WINE as a wrapper.

Thanks a lot, I knew about WINE and have decided that the games that I can play via wine I will but i will leave a M$ install for Crysis and unsupported software that i'm taking a catalog of from my computer.

---

