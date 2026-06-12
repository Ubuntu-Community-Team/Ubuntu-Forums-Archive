---
title: "can't configure bridge network for static IPs"
date: 2010-08-12
forum: Virtualisation
---

### Post by jbcolmena on 2010-08-12
Hi all:

I'm runing ubuntu server 9.10, and have two VM runing ubuntu jeos on it (KVM). I want to be able to connect directly to the VMs from home -or any place really-.

I have three static IPs. One for the server, two for the VMs. But I'm really going crazy with the network configuration... all the manuals and tutorials I find refer to one machine using dhcp, so, what if I have several VMs each with a static IP address using KVM? how do I configure that? any light on this would be greatly appreciated...

---

### Post by TheFu on 2010-08-16
> **jbcolmena said:**
> Hi all:

I'm runing ubuntu server 9.10, and have two VM runing ubuntu jeos on it (KVM). I want to be able to connect directly to the VMs from home -or any place really-.

I have three static IPs. One for the server, two for the VMs. But I'm really going crazy with the network configuration... all the manuals and tutorials I find refer to one machine using dhcp, so, what if I have several VMs each with a static IP address using KVM? how do I configure that? any light on this would be greatly appreciated...

Are your static IPs public or private?

The output of `ifconfig -a` and `brctl show` and the contents of your  /etc/network/interfaces from the hostOS would be a good place to start.

---

