---
title: "VirtualBox extra nic for guest"
date: 2008-07-10
forum: Virtualisation
---

### Post by self-defence on 2008-07-10
Hi,

I have VirtualBox installed on an Ubuntu host system and this host system has three network cards one is for the connection to the internet the other two nics are there for the guest systems. But I don't know how to connect the real network card to the VirtualBox guest system. I've tried to enter just eth1 in the place where there is a field for Host Interface Name.... but it says that no NIC attached or something.

So how do I get the networking working since I would like connect the virtual machine to another switch.

Thanks for the help.

Bye

---

### Post by bluefrog on 2008-07-11
create a bridge and a host interface bridged to eth1 (if it's the card you want to plug in another switch)

---

### Post by self-defence on 2008-07-11
Hey thanks,

I've found that I'm supposed to set up a bridge. But I'm having trouble I don't seem to know exactly how I'm supposed to setup the bridge and what to enter into VirtualBox.

Bye

---

