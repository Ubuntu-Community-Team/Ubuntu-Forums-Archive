---
title: "Network don't work on host, VM's has perfect network"
date: 2013-01-02
forum: Virtualisation
---

### Post by Denbert on 2013-01-02
Hi,

I'm having a strange issue with networking - I can't ping or use network on host machine, but networking is perfect on VM's?

Network /etc/network/interfaces has the following config:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 78.109.214.17
        netmask 255.255.255.240
        network 78.109.214.0
        broadcast 78.109.214.31
        gateway 78.109.214.30
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```

Anyone got a clue to put me in the correct direction?

---

### Post by Denbert on 2013-01-02
Hmm...

Solved by adding DNS server to the config file:

```

auto br0
iface br0 inet static
        address 78.109.214.17
        netmask 255.255.255.240
        network 78.109.214.0
        broadcast 78.109.214.31
        gateway 78.109.214.30
        dns-nameservers 208.67.222.222 208.67.220.220
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```

---

