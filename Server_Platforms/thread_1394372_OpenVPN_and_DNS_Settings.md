---
title: "OpenVPN and DNS Settings"
date: 2010-01-30
forum: Server Platforms
---

### Post by rmccarri on 2010-01-30
Hi,
I'm trying to get a VPN server running on my home desktop/server.  I used the tutorial here:

[https://help.ubuntu.com/community/OpenVPN]("https://help.ubuntu.com/community/OpenVPN")

I had to add:

```
push "redirect-gateway def1"

```

to my server.conf file in order to get it to work properly.  The OpenVPN server is functioning well, but now, I have the problem that the desktop computer that's serving up the VPN connection does not have anything in the /etc/resolv.conf file and cannont resolve any host names.

There is a script that is suppoesd to update the resolv.conf file that is supplied in the /etc/openvpn directory called update-resolv-conf.

At the top of this file, it says the following:

```

#!/bin/bash
# 
# Parses DHCP options from openvpn to update resolv.conf
# To use set as 'up' and 'down' script in your openvpn *.conf:
# up /etc/openvpn/update-resolv-conf
# down /etc/openvpn/update-resolv-conf

```

As per the Ubuntu tutorial, I created up.sh and down.sh and have those directed from the server.conf file.

Has anyone else been able to figure out how to use the update-resolv-conf script properly with the configuration detailed in the Ubuntu tutorial?

Any help would be greatly appreciated!
Rob

---

### Post by rmccarri on 2010-02-01
As inevitably happens when I post on here, the several days of unsuccessful searching prior to the post gave way to a few minutes of successful searching after.  Here is the fix that I guess should have been obvious before.

I added:

```
dns-nameservers 192.168.77.1 # my router DNS server
```

to /etc/network/interfaces under the br0 information to give the following interfaces file:

```
## Start these interfaces on boot
auto lo br0

iface lo inet loopback

iface br0 inet static
  address 192.168.77.100
  netmask 255.255.255.0
  gateway 192.168.77.1
  dns-nameservers 192.168.77.1
  bridge_ports eth0

iface eth0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  up ip link set $IFACE promisc on
  down ip link set $IFACE promisc off
  down ifconfig $IFACE down

```

---

