---
title: "kvm virtual network"
date: 2009-02-27
forum: Virtualisation
---

### Post by slavik on 2009-02-27
How/where can I define a virtual network for KVM? When I try to create VMs through virt-manager, the virtual network list is empty.

EDIT: figured it out ... you have to run virt-manager through sudo and it will allow you to create virtual networks

---

### Post by bodhi.zazen on 2009-02-28
+1 KVM

Yes, IMO that is an issue I have with virtmanager, some features are only available if you are running as root.

The other options are to use NAT or manually configure the host to act a a router, both of which take a little more effort.

---

### Post by dendrobates on 2009-03-03
> **bodhi.zazen said:**
> +1 KVM

Yes, IMO that is an issue I have with virtmanager, some features are only available if you are running as root.

The other options are to use NAT or manually configure the host to act a a router, both of which take a little more effort.

It should be enough to be in the libvirtd group.  Can you try adding yourself to the group, logging back in and see if that fixes it?

Rick

---

