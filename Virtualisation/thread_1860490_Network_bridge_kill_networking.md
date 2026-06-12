---
title: "Network bridge kill networking"
date: 2011-10-14
forum: Virtualisation
---

### Post by iburry on 2011-10-14
I've been vainly trying to set up a network bridge on my Ubuntu server 11.04 machine, but each time I configure it, networking breaks down completely. I've followed directions from several places (including the stickied thread above), but the results are always the same: no networking at all until I remove the bridge definition in /etc/network/interfaces.

My interfaces file:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# Add a tap
auto tap0
iface tap0 inet manual
tunctl_user roger

# Add a second tap
auto tap1
iface tap1 inet manual
tunctl_user roger

auto br0
iface br0 inet dhcp
        bridge_ports eth0 tap0 tap1
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
        # Uncomment the following line if you need to put your
        # network card into promiscuous mode.
        #pre-up ip link set eth0 promisc on
```This interfaces file is the most current attempt. I don't really know if the taps are still necessary. Not all source seem to use them.

---

### Post by iburry on 2011-10-15
Well, figured it out myself.  See what happens when you don't help out? I actually end up having to learn something.  I hope you can live with yourselves :)

Anyway, the following interfaces file does the trick:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# da bridge def
auto br0
iface br0 inet dhcp
        bridge_ports eth0 
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp on
```

---

