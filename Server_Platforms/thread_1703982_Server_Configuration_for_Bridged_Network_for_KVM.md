---
title: "Server Configuration for Bridged Network for KVM"
date: 2011-03-10
forum: Server Platforms
---

### Post by nubfilter on 2011-03-10
Hi all,

I've been googling and I haven't found anything exactly showing what to do here.

I have a server with a single NIC, and 5 IP addresses.
/etc/network/interfaces is setup as follows:
```

# Loopback
auto lo
iface lo inet loopback

#Primary IP address
auto eth0
iface eth0 inet static
address ipaddress1
netmask 255.255.255.0
gateway mygatewayaddress

#Additional IP addresses
auto eth0:0
address ipaddress2
netmask 255.255.255.0

auto eth0:1
address ipaddress3
netmask 255.255.255.0

auto eth0:2
address ipaddress4
netmask 255.255.255.0

auto eth0:3
address ipaddress5
netmask 255.255.255.0
```

I want to create 4 virtual guests on this machine, each with it's own IP address that is bridged to the public. the physical machine will have ipaddress1, and each guest will have one of the remaining IP addresses.

I tried to use brctl to add a bridge, then add eth0:0 to it and I was locked out of my machine, which required console access to resolve.

Do I need to setup multiple bridges for each IP? Am I able to setup the bridge(s) so that eth0 is not in the bridge, but eth0:0-4 are?

---

