---
title: "Different network cards for different virtual machines in KVM"
date: 2008-10-11
forum: Server Platforms
---

### Post by vprints on 2008-10-11
Hi, i'm trying to set up a Hardy server with 4 physical network cards, one for the host and three others each dedicated for one virtual machine.
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM) Talks all about bridging through one card, but how do I assign different dedicated network cards to different virtual machines?

---

### Post by promodus on 2008-10-12
[http://www.intel.com/technology/virtualization/](http://www.intel.com/technology/virtualization/)
There are network cards that support VT (VT-c)

What are you using for virtualization?

---

### Post by vprints on 2008-10-13
Hi, thanks for answering!
For virtualization i'm using KVM, for network cards NS DP83815, Intel 82571EB, and integrated motherboard chip: [http://h50281.www5.hp.com/sbs/sbserver/ml115/ml115_specifications.html](http://h50281.www5.hp.com/sbs/sbserver/ml115/ml115_specifications.html)

It seems that none of those network cards support any special virtualization technology, or does it only count whether my processor supports it (it should) ?

---

### Post by Blinkiz on 2008-10-23
> **vprints said:**
> Hi, i'm trying to set up a Hardy server with 4 physical network cards, one for the host and three others each dedicated for one virtual machine.
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM) Talks all about bridging through one card, but how do I assign different dedicated network cards to different virtual machines?

The only solution at the moment is to create a bridge (virtual switch) for each physical network card. Then you attach your virtual machines as you like to each bridge (switch). Meaning, you will end up having 4 brX interfaces, 4 ethX interfaces and a bunch tap interfaces for your virtual machines.

> **promodus said:**
> [http://www.intel.com/technology/virtualization/](http://www.intel.com/technology/virtualization/)
There are network cards that support VT (VT-c)
I don't really know what you are talking about. Maybe you have heard about assigning PCI devices directly to a virtual machines. Yes, it will be possible with an upcoming version of KVM (kvm-78 or kvm-79) and the new Intel Core i7 processor. So the feature is not yet here.

---

