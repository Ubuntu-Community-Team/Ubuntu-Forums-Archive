---
title: "AD Samba4, no resolving/ping domain name @18.04.2 Server"
date: 2019-06-03
forum: Server Platforms
---

### Post by fauxkalel on 2019-06-03
I am trying to setup Samba Active Directory domain. I followed tutorial on [https://www.tecmint.com/install-samba4-active-directory-ubuntu/](https://www.tecmint.com/install-samba4-active-directory-ubuntu/). Very good guide but still have a problem with step 16. I tried many things, but when using Ubuntu Server 18.04.2 (with alternative installer that is probably same as with standard 16.04), and configuring netplan, etc., i cant ping domain name even on server machine.
What steps need to be done on 18.04.2 (netplan) to start working resolving domain name?
——————————————–
ping -c3 jakisserwer
PING JakisSerwer.Business (127.0.1.1) 56(84) bytes of data.
——————————————–
ping -c3 jakis.lan
ping: jakis.lan: Name or service not known
——————————————–
krb5.conf:
[libdefaults]
default_realm = JAKIS.LAN
dns_lookup_realm = false
dns_lookup_kdc = true
——————————————————–
etc/hosts:
127.0.0.1 localhost
127.0.1.1 JakisSerwer.Business JakisSerwer


# The following lines are desirable for IPv6 capable hosts
::1 localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
—————————————————————–
resolv.conf:
nameserver 127.0.0.1
nameserver 192.168.0.77
search jakis jakis.lan office
———————————————————————-
netplan:


# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
version: 2
renderer: networkd
ethernets:
eno1:


dhcp4: no
addresses: [192.168.0.77/24]
gateway4: 192.168.0.1
nameservers:
search: [jakis, jakis.lan]
addresses: [127.0.0.1, 192.168.0.77]
————————————————————————-

---

