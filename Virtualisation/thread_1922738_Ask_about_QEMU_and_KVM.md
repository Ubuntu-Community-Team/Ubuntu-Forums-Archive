---
title: "Ask about QEMU and KVM"
date: 2012-02-09
forum: Virtualisation
---

### Post by feeliwood on 2012-02-09
I`ve searched for many documents about KVM and QEMU and some of the documents say that KVM can not create a Virtual Machine without QEMU, and some of them say that QEMU only handle the I/O task of VMs
so can someone please explain what exactly QEMU does when I combine KVM with QEMU.
I tried to create a VM with KVM, without QEMU and I succeed.
by the way, I`m using Ubuntu Server 11.10
thanks for any supports :D

---

### Post by coffeecat on 2012-02-09
*Thread moved from Ubuntu Translations to **Virtualization**.*

---

### Post by feeliwood on 2012-02-12
someone please help :(

---

### Post by rupert160 on 2012-02-16
From Wikipedia: Kernel-based Virtual Machine (KVM) is a virtualization infrastructure for the Linux kernel. QEMU is a processor emulator. KVM is a Linux kernel module that allows a user space program access to the hardware virtualization features of various processors, with which QEMU is able to offer virtualization for x86, PowerPC, and S/390 guests. When the target architecture is the same as the host architecture, QEMU can make use of KVM particular features, such as acceleration.

As a process:
Ensure your hardware has Hardware virtualisation extensions enabled on the CPU - A bios upgrade may be required to enable the CPU.
Then Layer qemu(command line) and if you want a GUI, aqemu to manage the vm's.

---

