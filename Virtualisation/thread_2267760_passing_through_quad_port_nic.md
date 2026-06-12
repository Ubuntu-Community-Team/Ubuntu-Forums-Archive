---
title: "passing through quad port nic"
date: 2015-03-03
forum: Virtualisation
---

### Post by sivel27 on 2015-03-03
hello all !

my google-fu is apparently lacking. i would like to setup a ubuntu desktop with 4-5 kvm or qemu guests. 
is it possible to pass through a quad port intel pt nic ? as so far as assigning each vm a physical port
on the single quad port switch ?

my thinking behind this was to get the best of both worlds -  vms and network "physicality", so i can learn
how to use a managed switch i purchased on ebay. if this is possible, is it feasible to do ?


thanks in advance,
sivel27

---

### Post by KillerKelvUK on 2015-03-04
You won't be able to achieve PCI pass through for a single device to 4 virtual machines simultaneously.  But from what you say you need I don't think pass through is what you want.  If you use the NIC within your host it will provide 4 different adapters e.g. eth0-3...you can then associate specific vm's to a specific ethx adapter and use bridging, granted the IP topology would be different to having the NIC physically owned but if this is about testing the managed features of your switch that shouldn't matter.  If you need specific network protocol support from the host into the vms and back such as 802.1q / VLANs (i.e. not just from managed switch port to managed switch port) then you'll need to look at using something like openvswitch as I don't believe linux-bridge has those features.

---

### Post by sivel27 on 2015-03-04
thank you for replying.

is it possible to pass though one single nic per vm ?

thanks again,
sivel27

---

### Post by KillerKelvUK on 2015-03-04
I guess, if you have 4 separate NIC's you could pass through one NIC to one specific VM and another NIC to another and so on.  You may possibly get into issues with IOMMU groups where 2+ NICs are in the same IOMMU group and you require all your VMs to be running at once...this hits an issue that so far can only be resolved by building a custom kernel after patching for ACS Override.  <--maybe look to validate this from others feedback as I'm applying my research into VGA pass through to your NIC scenario and some of it may not be valid.  If you already have a couple of NICs its an easy test but if you'd need to go out and buy them I'd seek some corroboration first.

I found a shell script somewhere (can't remember where to link it) which outputs your assignable devices per IOMMU group, use this to check.

---

