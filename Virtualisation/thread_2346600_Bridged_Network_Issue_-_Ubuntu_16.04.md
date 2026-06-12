---
title: "Bridged Network Issue - Ubuntu 16.04"
date: 2016-12-16
forum: Virtualisation
---

### Post by jpjackson8531 on 2016-12-16
I am having an issue setting up a bridge for my KVM guests. I have set up the bridge, br0, in /etc/network/interfaces and linked it to my network interface, eno1. When I bring it up using brctl, it shares the ip with eno1. However, when I bring it up, the host loses network connectivity. I can't get out to the Internet with the host machine nor can I ssh into it locally.

Because  the server has two network cards, I used a switch and attached both to  the router. Running ifconfig, the bridge is still  sharing 192.168.1.16 with eno1, and eno2 now has it's own ip 192.168.1.17. However, the host still can't get out and I can't ssh in.  
 
 Looking at my router's  configuration, there is no device leasing 192.168.1.16, and 192.168.1.17  is now listed as the bridge connection (it was 192.168.1.16 before connecting the second NIC to the router).

How can I keep the host's network connection when bringing up the bridge, or how can I re-establish it after I bring it up? I've done a lot of searching but can't seem to figure it out.

---

### Post by TheFu on 2016-12-16
Welcome to the forums.

a) please use standard fonts.
b) please post the interfaces file using "code tags" so things line up as expected.
c) please post the output from **ifconfig** and **route -n** - code tags again, please.

You don't want static IPs set inside the range that a DHCP server expects to be available. Don't do that.
Cheap routers don't like it when we connect 2 NICs from the same computer to them. You need a "managed switch" or perhaps redundant routers running VRRP (or whatever that router vendor calls it), most likely, if they are on the same subnet.

Do you intend to use both NICs from the same OS on the same subnet?  I've always put different NICs on different subnets (SAN vs LAN vs Mngt). I've only played with bonding. At work, we have Linux guys that do all that stuff.

---

### Post by howefield on 2016-12-16
Thread moved to the "*Virtualisation*" forum.

---

