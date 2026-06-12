---
title: "Access host OpenVPN tap0"
date: 2012-12-22
forum: Virtualisation
---

### Post by JoeSabido on 2012-12-22
I have a computer running Ubuntu 12.04 64bit, which uses OpenVPN and a TAP adapter to connect to a VPN server.

This computer runs VirtualBox in which I have a virtual machine running Ubuntu 10.04

Is there a way to make the Virtual Machine to access the computers in the VPN network?

The network card of the Host is already accessible to the Guest, and the Guest gets an IP address from my router and gets internet access.

Thanks

---

### Post by teeks99 on 2012-12-23
I haven't done it with virtual box, but I have with KVM. The trick was making a bridge with tap0.  Here's the full writeup of what I did:
[http://teeks99.com/sys/OpenVPN-VMs/Tryout.html]("http://teeks99.com/sys/OpenVPN-VMs/Tryout.html")

---

### Post by JoeSabido on 2012-12-23
Thanks teeks,

That's the first thing I thought, exposing the tap0 interface to the VM and making it bridged, but that didn't work in VirtualBox, I'll try KVM on Monday and see what happens.

Thanks :)

---

