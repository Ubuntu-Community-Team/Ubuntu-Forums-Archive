---
title: "network connection"
date: 2010-01-19
forum: Server Platforms
---

### Post by klompie on 2010-01-19
I installed Ubuntu Server 9.04 64-bit today. Only option slected during installation was SSH.
Everything worked fine, i configured a static IP, installed updates, installed vmware server, and rebooted.

But now my internet connection is gone:(

How can I solve this?

when i try to ping another pc on my network it returns "Destenation Host unreachable"

my network config:
auto eth0
iface eth0 inet static
address 192.168.1.111
gateway 192.168.1.254
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

---

