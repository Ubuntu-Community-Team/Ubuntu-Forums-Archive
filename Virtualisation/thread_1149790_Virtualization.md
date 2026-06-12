---
title: "Virtualization"
date: 2009-05-05
forum: Virtualisation
---

### Post by yazidarezki on 2009-05-05
I am using ubuntu 9.04 and KVM, I have a VM and installed Windows server 2008. Ubuntu recognises the CD/DVD but the VM does not recognise it. If I put DVD or CD in the VM it still thinks there is no DVd in.
 
Any idea why?
 
TIA
Yaz

---

### Post by veloce on 2009-05-07
> **yazidarezki said:**
> I am using ubuntu 9.04 and KVM, I have a VM and installed Windows server 2008. Ubuntu recognises the CD/DVD but the VM does not recognise it. If I put DVD or CD in the VM it still thinks there is no DVd in.
 
Any idea why?
 
TIA
Yaz

Couple of things:
If the disk has been mounted by Ubuntu it may not be available to the vm.
I can't get a blank disk to be recognised - maybe that's not supported?

How are you connecting to the disk?  I use virt-manager and find the hardware screen to be reasonably straight forward.  When the disk is unavailable to the vm the real device is greyed out.

---

### Post by yazidarezki on 2009-05-11
I have VM and then I put Windows 2008 in Cd/dvd it (VM) recignises it and installs, then I installed few more things it (VM) recognises the CD/DVD rom.Then all of a sudden when I put a CD/DVD the VM does not recognise it.

---

### Post by veloce on 2009-05-11
Couple of things:
If the disk has been mounted by Ubuntu it may not be available to the vm.

I can't get a blank disk to be recognised - maybe that's not supported?

How are you connecting to the disk? I use virt-manager and find the hardware screen to be reasonably straight forward. When the disk is unavailable to the vm the real device is greyed out.

---

