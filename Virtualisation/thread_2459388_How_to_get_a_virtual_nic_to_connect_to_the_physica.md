---
title: "How to get a virtual nic to connect to the physical nic (virt-manager)"
date: 2021-03-17
forum: Virtualisation
---

### Post by remag03 on 2021-03-17
Hi I am running ubuntu server on virt-manager, I am very comfortable with VMWare but I do not understand virt-manager well. 

When I do ifconfig in the virtual server I see there is a NIC and a loopback I do not know how to get this NIC to connect to my host machine's NIC. 

Also when I do ifconfig on my host machine I see there is a virtual NIC and virtual loopback from virt manager as well as the host machine NIC and loopback. 

I want the virtual server to connect directly to the host machine physical NIC. How do I do this?

---

### Post by Regexaurus on 2021-03-26
Uhh, Ubuntu Server doesn't "run" on virt-manager. Virt-manager is a utility for managing KVM VMs, but can also manage Xen VMs and LXC (Linux containers). I think you'll need to offer more information about your virtualization environment/platform, before anyone can offer reasonable suggestions...

---

