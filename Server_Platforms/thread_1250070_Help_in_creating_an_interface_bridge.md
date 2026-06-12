---
title: "Help in creating an interface bridge"
date: 2009-08-26
forum: Server Platforms
---

### Post by dragos2 on 2009-08-26
This is current network configuration:

/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
        address 193.19.*.*
        netmask 255.255.255.0
        network 193.19.*.*
        broadcast 193.19.*.*
        gateway 193.19.*.*
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 193.19.*.*
        dns-search theserversdomain.com

```
How should I adapt the instructions from here
[http://ubuntuforums.org/showthread.php?p=3798970#post3798970](http://ubuntuforums.org/showthread.php?p=3798970#post3798970) (the bridge section)
to my situation in order to create a bridge for openvz ?

---

