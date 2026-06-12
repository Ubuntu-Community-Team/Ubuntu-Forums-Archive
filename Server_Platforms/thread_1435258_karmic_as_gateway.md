---
title: "karmic as gateway"
date: 2010-03-21
forum: Server Platforms
---

### Post by -genin- on 2010-03-21
hello all...
I need some help...

at first I'll show my first desktop **(as PC1)** /etc/network/interfaces

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.2
gateway 192.168.1.1
netmask 255.255.255.0

auto eth0:0
iface eth0:0 inet static
address 172.18.2.2
netmask 255.255.0.0

and then, I have another desktop **(as PC2)**, this is the /etc/network/interfaces

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 172.18.3.3
netmask 255.255.0.0

this is the case...
I want to get internet connection on PC2 through PC1... (in this case PC1 has an internet connection via gateway 192.168.1.1)

can somebody help me... thx

---

### Post by noway2 on 2010-03-21
The simplest way to do this would be to use PC1 as a proxy.  Check out squid proxy, which is in the repositories.

---

### Post by jrssystemsnet on 2010-03-21
The real question is, what are you trying to accomplish?  PC1 only has one interface, so PC1, PC2, and the real gateway are clearly all on the same actual network.  What's your actual goal here, that is preventing you from just putting PC2 at 192.168.1.3 and running it through the real gateway as well?

---

### Post by -genin- on 2010-03-21
> **jrssystemsnet said:**
> The real question is, what are you trying to accomplish?  PC1 only has one interface, so PC1, PC2, and the real gateway are clearly all on the same actual network.  What's your actual goal here, that is preventing you from just putting PC2 at 192.168.1.3 and running it through the real gateway as well?

Yes, I'm just preventing because of limited IP.

---

