---
title: "Networking on KVM"
date: 2009-11-10
forum: Virtualisation
---

### Post by joseba on 2009-11-10
Hello:

My question is about my network

host:
-----
ubuntu with virtualization KVM
br0 bridge to eth0, connected to router adsl to internet.
br1 bridge to eth1, connected to access point to LAN

guest 1:
--------
firewall_1 --> wan: to br0
           --> lan: to next guest (squid)
guest 2:
--------
squid      --> wan: to lan in firewall_1
           --> lan: to br1

I need a virtual switch to connect the two guest.
I dont know how to connect squid and the firewall_1 (wan_squid to lan_firewall_1)
Is it possible to create a bridge without a physical connection to a ethernet card?,i mean, the same way a vmnet on vmware server.
The pc's in the lan wont have access to this virtual switch.

juanjoA
Un saludo / bye

---

