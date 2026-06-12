---
title: "64-bit Ubuntu, VirtualBox not detecting VT-x enabled."
date: 2010-06-27
forum: Virtualisation
---

### Post by slooksterpsv on 2010-06-27
Ok I've installed 64-bit OSes in VirtualBox before, and I'm running 64-bit Ubuntu, but when I try to start the VM it thinks that VT-x is disabled, but it's not. Do I need a separate kernel or what do I do to fix this?

Any help would be appreciated.

Last time the fix for it was, remove kvm and it worked, but removing kvm didn't work cause KVM, QEMU, or any other VT Programs aren't on here.

---

### Post by tgm4883 on 2010-06-27
Is this a new computer? I've noticed that some BIOS's have an option to disable this. I'd check there

---

### Post by slooksterpsv on 2010-06-27
It's enabled in BIOS, well can't disable it, by default its enabled for my Gateway NV53. I'm actually in Windows installing a 64-bit OS and it's working.

Not a biggy I usually run 32-bit OS'es in VM's I just had this iso of one and thought I would try it out (64-bit).

Any software that could be blocking 64-bit from being detected?

---

