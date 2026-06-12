---
title: "Ubuntu 12.04 beta2 with kernel 3.2 iommu not available"
date: 2012-04-09
forum: Virtualisation
---

### Post by neco on 2012-04-09
Hi!

I have installed the Precise pangolin beta 2 (ubuntu 12.04) and sadly noticed that i must disable the iommu support in the bios to be able to reach the login screen.

Also it dosent make any dmesg.log, when i cat it, is empty. So no idea how to debug it.

I tried with the kernel 3.3 with no luck.

My motherboard is a GA-990-FXA-UD3 with the latest bios.

I can run Virtualbox (less perfomance), but the programs cos i need to bypass devices like xen or kvm dont work at all without iommu enabled.

Any suggestion?

PD: Hope will be released a fully functional Ubuntu 12.04 with a kernel path ...

---

### Post by neco on 2012-04-09
Update:

I have checked and confirmed that it is not the kernel, nvidia propietary driver instead ...

So my way to their forums ...

---

### Post by sprucegum on 2012-05-10
Hey folks, try booting with the following kernel parameter: iommu=pt

This should allow you to use the iommu in the presence of an Nvidia card.

---

