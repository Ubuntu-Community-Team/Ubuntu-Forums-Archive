---
title: "Need a Fixed IP"
date: 2007-05-20
forum: Server Platforms
---

### Post by Luft on 2007-05-20
I have a Ubuntu 7.04 server that I just setup.  I need it to have a fixed IP address rather than getting a DHCP address.  How can I do this?

Thanks.

---

### Post by mitch.c on 2007-05-21
Change /etc/network/interfaces. Here's mine for example:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.250
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1
```

---

