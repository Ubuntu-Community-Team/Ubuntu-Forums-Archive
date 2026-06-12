---
title: "Hyper-V and Ubuntu Server VM = No network"
date: 2011-08-11
forum: Server Platforms
---

### Post by terek on 2011-08-11
Hello

I have Dell R410 with MS Hyper-V 2008 R2 as Host. On Host I have couple VM's (Win7, Win2k3) all work fine. Now i need Ubuntu VM so i create new VM with Legacy Network Adapter, 1024 Ram and 1vcpu. When i install Ubuntu 11.04 Server on VM he find network card and take ip from DHCP (192.168.1.185). After instalation i restart VM login as root and i don't have network. If I write ifconfig i see two network card eth0 and lo.

eth0 have IP address, mask, broadcast and gateway from DHCP Server.


Do you have any idea what is wrong ??


PS.Sorry for my english

---

### Post by kristenannie on 2011-08-26
We are having the same issues.  We've tried installing Ubuntu 8.04 with legacy network adapter and also 10.04 and get the same issues described above and are not able to connect to the network.  Anyone run into this and solve it?

Thanks so much!
Kristen

---

