---
title: "KVM guest router network"
date: 2014-11-01
forum: Virtualisation
---

### Post by karq12 on 2014-11-01
Hey,

I just moved from virtual box to KVM and I'm trying to figure out how to get my previous network working. I have installed Endian firewall as a guest who previously on my virtual box system shared the internal network for all my computers and other guests.Maybe someone can help me out how to configure same system on kvm? 

spec:
I have 2 physical network interfaces on my server eth0(wan) and eth1(lan)
internet -> eth0 -> endian - > eth1 ->vm host,other guests and pc's.

---

### Post by TheFu on 2014-11-02
For non-default networking, manually build any bridges you desire through editing the /etc/networking/interfaces. Because there are thousands of possible configurations (perhaps millions), reviewing the documentation for that file format and possible settings is strongly advised.
**man interfaces**

For a firewall running inside a VM, don't give the hostOS an IP on the "red" interface. Only let the firewall VM have that access. The hostOS and "green" interface on the firewall VM should be on the same internal LAN.

---

