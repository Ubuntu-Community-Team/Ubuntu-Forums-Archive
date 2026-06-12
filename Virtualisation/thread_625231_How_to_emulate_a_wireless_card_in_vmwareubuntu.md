---
title: "How to emulate a wireless card in vmware/ubuntu?"
date: 2007-11-27
forum: Virtualisation
---

### Post by ragas on 2007-11-27
Guest OS: Ubuntu Gutsy Gibbon 7.10 with kernel 2.6.16
Host OS: Windows XP with Dell 1390 wireless NIC

I want to set my network on Ubuntu to be using a wireless NIC (I don't care what it is). But I read in the VMWare Workstation documentation that the Ethernet card supported on guest OS is only AMD PCnet-PCI II Compatible. Right now, VMWare is using "Bridged:Connected directly to the physical network".

So, how do I emulate a wireless NIC in Ubuntu? Would appreciate any help in this regard.

---

### Post by Delvien on 2007-11-28
Im not sure if its possible to give the box direct control of your wireless NIC... now if you are connecting via Wireless and have your VM under bridged, all the data is being sent through your NIC anyway.

Im not quite sure why you want to do this.

---

