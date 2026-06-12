---
title: "No DNS resolution with IPv6 only"
date: 2017-01-30
forum: Server Platforms
---

### Post by kat8 on 2017-01-30
Can't seem to get name resolution working with a fresh 16.04.1 ipv6 only server install as a Hyper-V 2012R2 guest.

ping6, telnet work with other public hosts on the internet, but only using their ipv6 address, not by name
pinging this hosts ipv6 address from another datacenter on the internet returns good
apt-get works fine but only if I specify the ubuntu repo's ipv6 static addresses in /etc/hosts
resolv.conf contains the correct ipv6 name servers provisioned (2001:4860:4860::8844 and 2620:0:ccd::2)
dig -6 @2001:4860:4860::8844 returns "connection timed out; no servers could be reached" despite clean 2ms ping6 responses from that address
No firewall is currently up that would block the port
Other hosts (windows and centos) on the same switch have no such issues.

Feel like I'm missing something basic here but can't find it.

Interface Config
==============
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet6 static
   address [ipv6prefix]::ff
   netmask 64
   gateway [ipv6prefix]::1
   dns-nameservers 2001:4860:4860::8844 2620:0:ccd::2

---

### Post by kat8 on 2017-01-31
This issue appears to affect all IPv6 UDP traffic and was resolved by disabling transmit checksum offloading:

ethtool --offload  eth0  tx off

Checksum offloading does not seem to be an issue for TCP on IPv4 or IPv6, nor for UDP on IPv4.  However for IPv6 UDP traffic it is not working correctly.

---

