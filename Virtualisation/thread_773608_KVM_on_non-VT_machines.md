---
title: "KVM on non-VT machines"
date: 2008-04-29
forum: Virtualisation
---

### Post by undoIT on 2008-04-29
I was using Virtual Box before Hardy to run Windows XP for those few remaining programs I still need. On my Latitude D830, VT is enabled. However, on my XPS m1330 the CPU does not support VT. I tried installing KVM on the m1330 and I am able to start the install process using an ISO. The optical drive does not work for KVM. Any how, I get through the initial installation, but then it asks for the CD when KVM reboots Windows XP.

Anyhow, I am wondering if it is worth figuring out how to continue the installation processs with KVM. Or, is there no point in running KVM on a machine that does not have VT?

---

### Post by FredB on 2008-04-29
Well, it will be horribly slow without AMD-V or Intel-VT enabled processor. Just stay with virtual box. You'll find what you're looking for with it.

---

### Post by undoIT on 2008-04-29
On that note, how does KVM compare to Virtual Box? I'm going to put an install of Windows XP using KVM on my D830 tomorrow after slip-streaming SP3 in. I'm guessing there is a performance boost for kernel-based virtualization. I'd like to get USB support working, which isn't available with Virtual Box (as far as I know). I like the seamless mode and easy setup for a shared folder with my Linux host in Virtual Box.

---

### Post by FredB on 2008-04-29
It is a little harder to use KVM. For virtual box + usb, you won't find the code in the Open Source Edition of Virtual box.

And as KVM is based on qemu code, some options like enabling USB could be the same.

---

### Post by agent8131 on 2008-04-29
You can't use KVM without VT.  I would suspect that running "kvm" without VT just runs QEMU, which is slow but can be improved by installing the KQEMU kernel module.

VirtualBox OSE is easier to use than KVM but USB support is lacking.  Of course, you can install VirtualBox instead of VirtualBox OSE to get USB.  It's free as in beer as the license covers use for any single user.  The packages are available on the VirtualBox website.  So for ease of use I'd say that's the best choice.  If you need USB and want something open source then consider trying Qemulator as a front-end for KVM/QEMU.

---

