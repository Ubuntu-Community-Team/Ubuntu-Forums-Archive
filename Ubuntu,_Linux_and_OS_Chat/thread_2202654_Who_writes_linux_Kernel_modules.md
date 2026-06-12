---
title: "Who writes linux Kernel modules?"
date: 2014-01-30
forum: Ubuntu, Linux and OS Chat
---

### Post by mahela007 on 2014-01-30
I'm reading up on the linux kernel and I understand that linux kernel driver modules allow the OS to interact with devices on the computer (PC or mobile device, in the case of android). However, given the vast number of devices out there (hard drives, audio cards, graphics cards), it seems improbable that each one of them has a corresponding linux kernel module. Or, to put it another way, how is it that linux manages to run on so many platforms with a limited number of driver modules?

---

### Post by tgalati4 on 2014-01-30
Read the source code for a given module.  The modules themselves are huge, some supporting hundreds of devices.  Many modules support a particular chip (say a sound chip) and have software switches to support many variations of how the chip is wired up.  When the chip is used by many vendors you have hundreds of variations based on the same design.  So you get 80% of the functionality for most of this hardware, but that 20% have some problems or missing features.  Hence the time you spend here on the forums trying to fix stuff.

---

### Post by ssam on 2014-01-31
There is not really a distinction between kernel developers and module developers. Most drivers in linux can either be compiled into the kernel, or compiled as a module and loaded at run time. The kernels in distributions typically have near all drivers compiled as modules. Custom kernels (either built by a user or for a specific product) may only have a small number of drivers and have those compiled in.

I terms of who. there are several thousand developers committing code to the kernel. Have a look at [https://lwn.net/Articles/579081/](https://lwn.net/Articles/579081/) for some stats, included who imploys kernel developers.

---

