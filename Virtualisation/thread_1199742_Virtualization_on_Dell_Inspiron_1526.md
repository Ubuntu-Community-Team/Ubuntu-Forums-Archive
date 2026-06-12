---
title: "Virtualization on Dell Inspiron 1526"
date: 2009-06-29
forum: Virtualisation
---

### Post by chombium on 2009-06-29
Hi,

I've been struggling to setup virtualization on my Dell Inspiron 1526 laptop since version 7.10. It's an AMD Trurion 64 x2 with 2GB ram.

Until recently, for me, virtualization was a feature that was nice to have, but now it's a must. My past virtualization experiments on Ubuntu were complete failure. I've always thought that there is some bug that will hopefully get solved someday, AMD processor ](*,).... I also thought that due to the close cooperation between Dell and Canonical the processor won't be a problem :)

I spent my last weekend trying to make virtualization work on my Ubuntu 9.0, but with no success.

KVM, starts the virtual machine and when it should load the guest OS the laptop restarts.
QEMU and Virtual box, start and at some point while loading the guest OS the CPU usage rises to 100% and the whole laptop freezes.
I've checked the howtos in the virtualization mega thread, did everything from the very beginning, but nothing worked.
I've also tried to compile the latest KVM version from source but I ended up in segmentation fault when loading the kvm-amd kernel module :(

To check that the problem is not of hardware nature, I've tested KVM with Fedora 11 live USB and KVM worked without any problem.

I would appreciate if someone could help me debug/solve this problem. Due to the restarts of the laptop while testing the virtualization I can not find any traces in the logs.

I've been a happy Ubuntu user for ages, but now I'm thinking of moving to other distro due to the urgent need of vurtualization. :-?

---

