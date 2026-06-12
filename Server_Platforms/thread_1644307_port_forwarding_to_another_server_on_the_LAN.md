---
title: "port forwarding to another server on the LAN"
date: 2010-12-13
forum: Server Platforms
---

### Post by boondocks on 2010-12-13
We have a Ubuntu system that is connected to 4 different networks.
```
eth0: 192.168.12.9 
eth1: 192.168.2.142
tun0: 192.168.21.12
tun1: 192.168.45.8
```
On this system we would like to forward port 48080 such that:
```
192.168.12.9:48080   to  192.168.2.151:80
192.168.2.142:48080  to  192.168.2.151:80
192.168.21.12:48080  to  192.168.2.151:80
192.168.45.8:48080   to  192.168.2.151:80
```
In other words, everything for port 48080 forwards to 192.168.2.151:80

How can we do this so that it takes effect at boot time and is permanent?

---

### Post by HugoSerrano on 2010-12-13
Is your system only doing routing? Or is it firewall too? 
You can do that with IPTables.

---

### Post by HermanAB on 2010-12-13
Howdy,

You can use iptables redirect, or socat.

---

### Post by boondocks on 2010-12-13
> **HugoSerrano said:**
> Is your system only doing routing? Or is it firewall too? 
You can do that with IPTables.

Only routing.

---

### Post by boondocks on 2010-12-13
> **HermanAB said:**
> Howdy,

You can use iptables redirect, or socat.

With socat, how do you make it permanent?
So that it continues to do that after rebooting.

---

