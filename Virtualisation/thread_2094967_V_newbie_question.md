---
title: "V newbie question"
date: 2012-12-15
forum: Virtualisation
---

### Post by geohei on 2012-12-15
Hi.

Complete virtualization newbie question.

I got some new (desktop) hardware, Intel Core i7 3770K on Gigabyte GA-Z77X-UD5H, on which I would like to run tests with VMs.

Is it possible to run Ubuntu server together (!) with Windows 7 using the motherboards Intel Virtualization Technology? I would like to be able to switch between both worlds without being obliged to shutdown OS1 and reboot OS2 afterwards.

If possible, is there a guide somewhere how to setup such a box.

Thanks,

---

### Post by sandyd on 2012-12-15
> **geohei said:**
> Hi.

Complete virtualization newbie question.

I got some new (desktop) hardware, Intel Core i7 3770K on Gigabyte GA-Z77X-UD5H, on which I would like to run tests with VMs.

Is it possible to run Ubuntu server together (!) with Windows 7 using the motherboards Intel Virtualization Technology? I would like to be able to switch between both worlds without being obliged to shutdown OS1 and reboot OS2 afterwards.

If possible, is there a guide somewhere how to setup such a box.

Thanks,

hmm.
You probably want to check out KVM w/ virt-manager (if on a linux host) or VirtualBox (if on a windows host). You could also run something like ProxMox VE (you can access all VMs over network interface) or ESXi/XenClient (requires windows)

---

### Post by geohei on 2012-12-15
Thanks. Gonna do that. I'd like to avoid the "host" concept. Hence ESXi/vSphere attracts me. I have to check the hardware compatibility first.

If I run W7 and // Ubuntu (both as guests), are there performance drawbacks?

---

### Post by sandyd on 2012-12-16
> **geohei said:**
> Thanks. Gonna do that. I'd like to avoid the "host" concept. Hence ESXi/vSphere attracts me. I have to check the hardware compatibility first.

If I run W7 and // Ubuntu (both as guests), are there performance drawbacks?

Depends what you are short on. Two VMs shouldn't have a large impact, but when you start running a lot of VMs, your disk starts thrashing, assuming you don't hit the roof on CPU or Memory

---

