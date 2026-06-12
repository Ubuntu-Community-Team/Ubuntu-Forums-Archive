---
title: "Virtualbox VRDP"
date: 2008-10-17
forum: Virtualisation
---

### Post by PascalNobus on 2008-10-17
I've got a problem with Virtualbox
PC-1: Ubunty-hardy 192.168.2.6
PC-2: Ubuntu-hardy 192.168.2.3 with VirtualBox 2.0.2

Now I have an VM (XP) with IP 192.168.2.99.
I use Host Interface with name vbox0
On the VM I can surf the web.
On PC-1 and PC-2 I can ping 192.168.2.99.

But I can't make a vrdp-connection!

The network is setup by a bridge (br0) which connects
-eth0 192.168.2.3 (in promisc mode)
-vbox0

I followed several steps for setting it al up, but one thing I can't understand: I got br0, eth0, lo, vbox0 and tap0
Why the tap0? 


Hope someone can help me (it's not a wireless connection)

---

