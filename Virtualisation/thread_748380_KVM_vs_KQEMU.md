---
title: "KVM vs KQEMU"
date: 2008-04-07
forum: Virtualisation
---

### Post by gus_zernial on 2008-04-07
I'm running QEMU/WinXP under ubuntu 7.10 on a Core2 Duo which has hardware virtualization support. It works, but it's very slow and CPU use is high.

I'm confused as to what modules should be loaded - qemu? kqemu? kvm? kvm-intel? kqemu? Is the kqemu accelerator an alternative to kvm/kvm-intel, or are they used together?

Also, this system has an Nvidia 8600GTS, and I'm using Nvidia proprietary drivers for 
Linux, and Nvidia GL. Could that be a problem?

---

### Post by csi_ on 2008-04-07
kvm-intel is the module you need to load. read: [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)
kqemu is an alternative. read: [http://fabrice.bellard.free.fr/qemu/kqemu-doc.html](http://fabrice.bellard.free.fr/qemu/kqemu-doc.html)
You should get better perfs with KVM.
> **gus_zernial said:**
> Also, this system has an Nvidia 8600GTS, and I'm using Nvidia proprietary drivers for Linux, and Nvidia GL. Could that be a problem?
This should not be a issue.

---

### Post by gus_zernial on 2008-04-07
I was confused, this cleared it up. QEMU/KVM working *much* better now. Thanks for the help!

---

### Post by csi_ on 2008-04-08
You're welcome.
Don't forget to mark this thread as solved.

---

