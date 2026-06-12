---
title: "Problem running VirtualBox 3.2.8 r64453..."
date: 2010-08-11
forum: Virtualisation
---

### Post by mikey5555 on 2010-08-11
Hello all,
I have just re-installed Lucid (actually it is "Ultimate Edition 2.7" derivative of Ubuntu Lucid) and VirtualBox 3.2.8 r64453, and I am having problems opening/running the virtual machine.  When I attempt to start the VM, I get the following error:

> [b]Failed to open a session for the virtual machine Win_XP.
VirtualBox can't operate in VMX root mode. Please disable the KVM kernel extension, recompile your kernel and reboot (VERR_VMX_IN_VMX_ROOT_MODE).


Result Code: NS_ERROR_FAILURE (0x80004005)
Component:   Console
Interface:   IConsole {6375231a-c17c-464b-92cb-ae9e128d71c3}[/b]

I have attached a screenshot of the error dialogue, but it is not easily readable (see below), so the text of the error dialogue box is shown above
for clarity.
[ATTACH]166178[/ATTACH]

Anyone know how to correct this problem??  

Regards...
mikey5555

---

### Post by JustinR on 2010-08-14
Hi,

try removing package 'libvirt-bin' and restart your computer.

---

