---
title: "Virtualbox with Virtual Ip's does it work?"
date: 2008-12-12
forum: Virtualisation
---

### Post by supperman2k on 2008-12-12
I have 7 ips,

I am currently using 2 ips on the host machine, and I would like to setup virtual box to use a 3rd ip.

I currently specify the ips with eth0, eth0:1, eth0:2 etc. up to eth0:6

I have had nothing but problems with setting up the interfaces to bridge br0 with vbox0, and eth0:6

Is this even possible?

---

### Post by supperman2k on 2008-12-12
Here is my Setup for testing

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
         address 67.205.89.198
         netmask 255.255.255.224
         gateway 67.205.89.193
         bridge_ports eth0 vbox0

auto eth0:1
iface eth0:1 inet static
         address 70.38.4.193
         netmask 255.255.255.248


When I restart networking I get this error. I've attached a screenshot.

I have connectivity, but when resetting the network it is really slow, and the guest machine which is also running unbuntu, has no internet connections.

I have set the guest machines eht0 to the same settings as the br0 on the host machine.

---

### Post by Dedoimedo on 2008-12-14
Hello,

I'm not sure if this will work, but try:

Set static ip for all your interfaces eth0 through eth0:6. Then, try bridging with one of the virtual interfaces.

However, if I recall correctly, a bridge must have one physical interface ...

Dedoimedo

---

