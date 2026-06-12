---
title: "x86- 64 CPU needed but only detects i686 cpu"
date: 2015-11-28
forum: Virtualisation
---

### Post by klidjlidgmail.com on 2015-11-28
What does this mean?  My Virtual machine says, "This kernel requires an x86-64 CPU, but only detected an i686 CPU.  Unable to boot - please use a kernel appropriate for your cpu". :mad: I can't download Ubuntu into my Virtual machine.  Any idea on what I should do?  Thank you in advance!

---

### Post by grahammechanical on 2015-11-28
To put it simply i686 = an Intel 32 bit CPU.

If your machine is running on an Intel 32 bit CPU and you are setting up a Virtual Machine to run Ubuntu in, then must must download and use the Ubuntu 32bit ISO image and not the 64 bit ISO image.

If things were the other way around, with the machine running on an Intel 64 bit CPU, then Ubuntu 32 bit would run in that VM as well as 64 bit Ubuntu. The architecture of an Intel 64 bit CPU is backwards compatible with the architecture of Intel 32 bit CPUs. This means that a 32 bit OS will run on a 32 bit CPU and a 64 bit CPU. But a 64 bit OS will only run on a 64 bit CPU.

A Virtual Machines use the hardware of the host machine. So, you have an incompatibility caused by trying to run a 64 bit OS in a VM running on a 32 bit CPU. That is my guess.

Ubuntu i386 ISO = 32 bit Ubuntu OS. Ubuntu amd64 ISO = 64 bit Ubuntu OS. Oh, amd64 ISO will run on Intel 64 bit CPUs and not only AMD 64 bit CPUs.

Regards.

---

### Post by mastablasta on 2015-12-01
also if you do have 64bit CPU on computer, to run 64bit OS in virtualbox you need to enable virtualization in BIOS/UEFI. : [https://www.virtualbox.org/ticket/12458?cversion=5&cnum_hist=10](https://www.virtualbox.org/ticket/12458?cversion=5&cnum_hist=10)

VT-x or AMD-V (depending on CPU manufacturer) has to be enabled.

---

### Post by deadflowr on 2015-12-01
Moved to Virtualisation

---

