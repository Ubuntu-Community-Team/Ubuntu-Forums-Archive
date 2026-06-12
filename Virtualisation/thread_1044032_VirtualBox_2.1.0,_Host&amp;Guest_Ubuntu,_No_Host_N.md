---
title: "VirtualBox 2.1.0, Host&amp;Guest: Ubuntu, No Host Networking"
date: 2009-01-19
forum: Virtualisation
---

### Post by efm on 2009-01-19
Hello,
I'm using VirtualBox 2.1.0 in Ubuntu 8.10 as host, with a guest also
Ubuntu. I've selected the Host Networking and selected eth0 in network
tab, but when I started the guest and set the ip address (using 
ifconfig eth0 192.168.1.2, as the host is 192.168.1.1), I can't ping
the host (and host itself can't ping the guest). 

previously I used VirtualBox 2.0.4 with bridging. When I upgraded to 2.1.0,
I commented out all lines related to bridging in /etc/network/interfaces.

can someone help me?
thank you

---

### Post by mikewhatever on 2009-01-19
Why not use DHCP? 192.168.1.2 is your router's address, which the guest has no direct access to.

---

