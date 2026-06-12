---
title: "Heterogeneous Network Server Server Hang (Incorrect settings /etc/network/interfaces)"
date: 2014-04-14
forum: Server Platforms
---

### Post by sharkey77 on 2014-04-14
Getting the infamous "waiting 60 more seconds for network configuration" but I'm mixing WAN and LAN ip's so can't find a solution.

I'm willing to bet my file is incorrect.

All ip's work.  The system just hangs on boot temporarily and I can't find documentation on mixing gateways.

/var/log# cat /etc/lsb-release
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS"
```

/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address **.**.**.73
        netmask 255.255.255.248
        gateway **.**.**.78


auto eth0:1
iface eth0:1 inet static
        address 192.168.0.36
        netmask 255.255.255.255
        gateway 192.168.0.1

auto eth0:2
iface eth0:2 inet static
        address **.**.**.74
        netmask 255.255.255.248



# This is an autoconfigured IPv6 interface
iface eth0 inet6 auto
```

---

