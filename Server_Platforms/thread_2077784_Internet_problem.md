---
title: "Internet problem"
date: 2012-10-29
forum: Server Platforms
---

### Post by nikibg on 2012-10-29
Hi i wanna config internet to my ubuntu  but i have a problem 

after restart i must write ifup eth0 to start having internet

my /etc/network/interfaces is 
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.59
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.55
```
Why i  have to start it manually

---

