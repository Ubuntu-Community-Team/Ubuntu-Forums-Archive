---
title: "KVM memory &amp; CPU allocation"
date: 2014-05-14
forum: Virtualisation
---

### Post by redrumrogue on 2014-05-14
Hi all,

I'm just trying to to learn my way around KVM and using virt-manager.  I was just wondering - if I set Max Memory Allocation to 8192MB and Current Allocation to 2048MB for example, will the VM automatically take more memory if it needs it and release it when it's not needed?  Same with CPU allocation - if i set max allocation to 8 virtual CPUs and current allocation to 2 ....

Thanks,
JB

---

### Post by TheFu on 2014-05-14
Try it and let us know please. ;)  I'm curious too.
[http://libvirt.org/formatdomain.html#elementsCPUAllocation](http://libvirt.org/formatdomain.html#elementsCPUAllocation)
[http://libvirt.org/formatdomain.html#elementsMemoryAllocation](http://libvirt.org/formatdomain.html#elementsMemoryAllocation)

Relatively speaking, CPU and RAM are cheap, not worth risking stability over aggressive settings when the workload changes.
Since I don't use swap for most of my VMs, it just isn't worth it.

---

