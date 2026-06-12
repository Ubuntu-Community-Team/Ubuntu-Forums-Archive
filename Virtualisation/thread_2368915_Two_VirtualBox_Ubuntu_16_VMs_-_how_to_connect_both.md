---
title: "Two VirtualBox Ubuntu 16 VMs - how to connect both VMs to openvpn simultaneously"
date: 2017-08-16
forum: Virtualisation
---

### Post by crabbychicken on 2017-08-16
Hi,

Windows 7 host.

Virtualbox software running on host.

Ubuntu 16 Mate virtual machine.

I have installed openvpn in Ubuntu VM and can successfully connect to my paid vpn using the terminal command:

sudo openvpn us354.xxxxxxxxx.ovpn

I got it to work by changing my network settings to bridged adapter (from NAT which was default).

I can connect to the openvpn when a single VM is running.

Here is the problem....

I cloned the ubuntu virtual machine - now I have Ubu VM1 and Ubu VM2.

When both VMs are running at the same time I cannot connect to the openvpn vpn server.

I want to be able to run Ubu VM1 an Ubu VM2 at the same time and connect Ubu VM1 to openvpn vpn1 and connect Ubu VM2 to openvpn vpn2.

Any suggestions?

Thanks.

---

### Post by pavlo.m on 2017-08-17
Are you have same IP address and MAC on both VM? Do you have internet on both of them? (try ping 8.8.8.8)

---

