---
title: "connect: Network is unreachable"
date: 2011-02-28
forum: Server Platforms
---

### Post by acastrolorenzo on 2011-02-28
Hi everyone, 

I´ve just install and configure an 10.10 ubuntu server, but I cant  install anything from internet. When ping for example Google, recieves  "connect: network is unreachable". 

Route -n gives:
[COLOR=#000000][COLOR=#0000BB]192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0  

[/COLOR][/COLOR]/etc/network/interfaces is wrote as:
[COLOR=#000000][COLOR=#0000BB]iface eth0 inet [/COLOR][COLOR=#007700]static 

[/COLOR][COLOR=#0000BB]address 192.168.1.5 
netmask 255.255.255.0 
gateway 192.168.1.0  

[/COLOR][/COLOR]Any idea?

LOTS of thanks!

---

### Post by alarme on 2011-02-28
Can you post the output of?

ifconfig
cat /etc/resolv.conf

---

### Post by acastrolorenzo on 2011-02-28
I´ve solve it. Gateway IP was wrong. When listings your IPs on route -n, you have to take the second one. Thats it!

PD: Thanks alarme anyway

---

### Post by koenn on 2011-02-28
> **acastrolorenzo said:**
> Gateway IP was wrong. When listings your IPs on route -n, you have to take the second one. Thats it!

192.168.1.**0** is a network address. gateway needs to be a host address of a router -- very often that's 192.168.1.**1**

---

