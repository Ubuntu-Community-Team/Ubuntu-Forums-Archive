---
title: "Ubuntu 14.04 KVM Bridge configuration help."
date: 2014-10-03
forum: Virtualisation
---

### Post by Chris_Wisenbaker on 2014-10-03
I'm new to Linux and KVM. I've been searching for a while and don't know if I'm just wording this wrong but I can't seem to get my VM to Bridge and get an internal IP. Here is my setup.

Ubuntu Server 14.04 
Zentyal 3.5 is installed and running
KVM is installed
bridge utils is installed
I've installed Windows 7 as a VM (needed for some proprietary software)

here is my network config

auto lo br1 br1:vl1 eth0 eth1

iface lo inet loopback

iface br1 inet static
      address 192.168.0.2
      netmask 255.255.255.0
      broadcast 192.168.0.255
      bridge_ports eth0 eth1
      bridge_stp off
      bridge_waitport 5

iface br1:vl1 inet static
      address 192.168.0.3
      netmask 255.255.255.0
      broadcast 192.168.0.255

I've also configured the VM's config file to use the bridge, but for some reason when I run **arp -n** I see <incomplete> were there should be a mac address.

Any help is appriciated. If anyone needs more information please ask.

---

### Post by TheFu on 2014-10-04
Try:
bridge_ports eth0

[http://blog.jdpfu.com/ALE/ALE-NW/2014_04-virtualization.html](http://blog.jdpfu.com/ALE/ALE-NW/2014_04-virtualization.html) has more.
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
 address 192.168.0.2
# gateway is mandatory - point to your network gw
 gateway 192.168.0.200   
 netmask 255.255.255.0
# pick nameservers you like, trust
 dns-nameservers 8.8.8.8
 metric 1
 bridge_ports eth0
 bridge_fd 9
 bridge_hello 2
 bridge_maxage 12

```

---

