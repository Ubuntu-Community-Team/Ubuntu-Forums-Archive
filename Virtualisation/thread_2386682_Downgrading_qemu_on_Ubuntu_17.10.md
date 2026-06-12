---
title: "Downgrading qemu on Ubuntu 17.10"
date: 2018-03-08
forum: Virtualisation
---

### Post by eezacque on 2018-03-08
I have been happily running qemu-system-x86_64 to create a virtual machine over the past 3 years, but it looks like the upgrade to Ubuntu 17.10 broke my virtual machine, as it falls into an infinite boot loop. This is an absolute showstopper for me, so I intend to go back to 16.04 if I need to. 

Is there any older version of qemu-system-x86_64 I can safely roll back to on Ubuntu 17.10, or is this asking for even more troubles?

---

### Post by kerry_s on 2018-03-08
it breaks gnome boxes to, which is what i use. i couldn't fix it either.

i might drop down to a ubuntu 16 as well. currently running fedora 27, cause it's what i had on usb.

---

### Post by C.S.Cameron on 2018-03-10
I have been playing with MultiBootUSB 9.1.0.
It comes with qemu-system-x86_64 which version seems to work with 17.10 OK.
It is booting both ISO's and flash drives.
So far QEMU seems awful slow, is this normal?

---

### Post by eezacque on 2018-03-10
> **C.S.Cameron said:**
> So far QEMU seems awful slow, is this normal?

I have used qemu to emulate a Mac with Photoshop, using a Wacom Cintiq, so I think performance is okay.

---

### Post by C.S.Cameron on 2018-03-10
> **eezacque said:**
> I have used qemu to emulate a Mac with Photoshop, using a Wacom Cintiq, so I think performance is okay.

Booting from qemu-kvm with virt-manager does run quite a bit faster than booted from the MBUSB QEMU GUI. 
17.10 boots OK for me from qemu-kvm, I think maybe I am over my head here.

---

### Post by eezacque on 2018-03-12
I downgraded to qemu-system-x86 1:2.5+dfsg-5ubuntu10 and my virtual machine is booting again.

---

### Post by eezacque on 2018-03-29
I rebuilt my virtual machine from scratch, and it looks the configuration of the Chimera bootloader is where things go wrong. That is, installing the OS, creating a bootable machine all works, but when I try to skip the bootloader menu, things go bump.

---

