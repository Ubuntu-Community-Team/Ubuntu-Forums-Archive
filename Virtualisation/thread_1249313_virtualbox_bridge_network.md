---
title: "virtualbox bridge network"
date: 2009-08-25
forum: Virtualisation
---

### Post by miklcct on 2009-08-25
I have 2 network adapters on the host:
eth0 static 192.168.0.1
eth1 dhcp

I set up some VMs to have bridge network on eth0. However, it does not work when the cable on eth0 is disconnected, it works when the cable is connected. What can I do to have the VMs work well on eth0 when the physical cable is disconnected (I want to simulate the effect that the VMs are connected to eth0 on the host as I am testing my LAN).

---

### Post by dmizer on 2009-08-25
Moved this to the virtualization section.

I have the same problem in vmware. I just plugged the cable into a hub and that solved the problem.

---

### Post by miklcct on 2009-08-27
Although I have a switch, it is connected directly to the Internet so I can't plug the cable directly into it as it is for an internal network. Every time I need to do this, I need to plug my cable into a laptop and connect the A/C adaptor for it.

---

