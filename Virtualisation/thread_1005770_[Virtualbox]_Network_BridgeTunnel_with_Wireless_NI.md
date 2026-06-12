---
title: "[Virtualbox] Network Bridge/Tunnel with Wireless NIC on a VLAN"
date: 2008-12-08
forum: Virtualisation
---

### Post by murmel on 2008-12-08
Hello everybody! I've been trying to get my network bridge to work and it does, on my own network.
But when I get to my school which uses multiple VLAN, it doesn't work.

I'm doing as [this]("http://www.savvyadmin.com/virtualbox-wireless-bridging-with-dhcp/") guide says.
My configuration at home is like this:
```
sysctl net.ipv4.ip_forward=1
tunctl -t tap0 -u murmel
ip addr add 192.168.0.150/32 dev tap0
ip link set tap0 up
parprouted wlan0 tap0
dhcrelay3 -i wlan0 -i tap0 192.168.0.1
route add -net 192.168.0.0 netmask 255.255.255.0 tap0
```
And it works fine using "Host interface" in Virtualbox (Debian as guest). But when I get to school and tries:
```
sysctl net.ipv4.ip_forward=1
tunctl -t tap0 -u murmel
ip addr add 192.168.54.150/32 dev tap0
ip link set tap0 up
parprouted wlan0 tap0
dhcrelay3 -i wlan0 -i tap0 192.168.54.1
route add -net 192.168.54.0 netmask 255.255.255.0 tap0
```
It doesn't work. I've noticed some error-messages about permission or something like that. I'll post the error messages tomorrow.

Is there something I have to do when I do this in a VLAN? Haven't read much about it.. Thanks!

---

### Post by Dedoimedo on 2008-12-09
Hello,

There could be many issues at hand:

Permissions, are you allowed to do what you want.
IPs, are they valid for the subnet / vlan you want to implement.
Maybe dhcp is disabled in your school?

Dedoimedo

---

