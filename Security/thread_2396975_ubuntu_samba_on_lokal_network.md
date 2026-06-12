---
title: "ubuntu samba on lokal network"
date: 2018-07-23
forum: Security
---

### Post by dogan226 on 2018-07-23
hello i am pretty new but am running ubuntu server with samba and can add users my question is that i want to use the server only on my local network and not to be able to acces through the internet from outside is it enough to set the server not up wiht dhcp ore dns  but lokal  ip adres to a local  number like 192.168.1.122 ore do i have to take more messurements ??
thnx

---

### Post by cariboo on 2018-07-24
Assuming you are behind a router, just use an ip address from your local sub-net, and don't do any port forwarding on your router. Having samba open to the world, is just asking to be hacked.

---

### Post by dogan226 on 2018-08-09
thanks i wil keep it only on the local network

---

