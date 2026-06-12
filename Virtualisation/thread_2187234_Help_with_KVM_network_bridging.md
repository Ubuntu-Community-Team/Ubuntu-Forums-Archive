---
title: "Help with KVM network bridging"
date: 2013-11-11
forum: Virtualisation
---

### Post by adriqn on 2013-11-11
OK so I am fairly new to KVM, after using VB the networking seems much more difficult. 
On  my host system I have 4 network cards:
eth0, eth1 and eth2 are bonded as bond0 on the LAN
eth3 is connected to the router and is allocated and address by dhcp
On guest 1 I have 2 network cards:
eth0 needs to bridge with host eth3 and obtain an IP by dhcp
eth1 needs to bridge with host bond0 and has a static IP
This guest is going to act as a gateway and dhcp server for the LAN

On guest 2 I have only one network card:
eth0 needs to bridge with host bond0 and obtain an IP by dhcp

The problem I have is that when I bridge any of the host connections with a guest, the host no longer has access to that connection.

Here's what the host interfaces file looks like at present:
```
# The loopback network interface
auto lo br0 eth3 eth0 eth1 eth2 bond0
iface lo inet loopback

# The primary network interface
iface eth3 inet dhcp

iface eth0 inet manual
bond-master bond0

iface eth1 inet manual
bond-master bond0

iface eth2 inet manual
bond-master bond0

iface bond0 inet static
        address 10.0.0.1
        netmask 255.255.255.0
        broadcast 10.0.0.255
        network 10.0.0.0
        bond-mode 4
        bond-miimon 100
        bond-updelay 100
        bond-lacp-rate 1
        slaves eth0 eth1 eth2

iface br0 inet static
        address 10.0.0.2
        netmask 255.255.255.0
        network 10.0.0.0
        broadcast 10.0.0.255
        bridge-ports bond0

```

I have tried to add a virtual interface to the host eth3 without success.

What am I missing here?  Or do I simply need to add an additional 2 cards to the host, one to the router and on to the LAN?

Thanks

---

### Post by TheFu on 2013-11-11
My networking is not nearly as complex as yours, however, the bridge stanza seems to be missing 
```
 bridge_fd 0
 bridge_hello 2
 bridge_maxage 12
 bridge_stp off
```

Does /proc/net/bonding/bond0  show anything useful?
What about  **brctl show**?

---

### Post by houstonbofh on 2013-11-11
I think you are getting bridging, bonding and routing confused.

Bonding is link aggregation, pr LACP.  It allows you to connect several nics to a LACP capabal switch for aggragation and the potential for additional bandwidth.

Bridging is a layer two connection, essentially turning several nics (or virtual nics) into a switch.

Routing is the connection of separate collision domains.  It now usually includes things like NAT.  The adapter virbr0 is the front end to a routed network.

Now you can bond a guest to any defined vswitch, which stock is virbr.  If you set up bridging [https://help.ubuntu.com/community/KVM/Networking#Bridged_Networking](https://help.ubuntu.com/community/KVM/Networking#Bridged_Networking) on a real interface, you can bind a gues to that, and they will be on the local network directly.

---

### Post by adriqn on 2013-11-12
> **houstonbofh said:**
> I think you are getting bridging, bonding and routing confused.

Bonding is link aggregation, pr LACP.  It allows you to connect several nics to a LACP capabal switch for aggragation and the potential for additional bandwidth.

Bridging is a layer two connection, essentially turning several nics (or virtual nics) into a switch.

Routing is the connection of separate collision domains.  It now usually includes things like NAT.  The adapter virbr0 is the front end to a routed network.

Now you can bond a guest to any defined vswitch, which stock is virbr.  If you set up bridging [https://help.ubuntu.com/community/KVM/Networking#Bridged_Networking](https://help.ubuntu.com/community/KVM/Networking#Bridged_Networking) on a real interface, you can bind a gues to that, and they will be on the local network directly.
Why do you think that?  What I want to know is how to bridge over a bonded interface?

---

### Post by TheFu on 2013-11-12
> **adriqn said:**
> Why do you think that?  What I want to know is how to bridge over a bonded interface?

After drawing a picture of what you described, I was convinced you knew exactly what you wanted AND I believe it is possible (barring any bugs).

Did you happen to run that command and look at the file in /proc?

---

### Post by houstonbofh on 2013-11-12
> **adriqn said:**
> Why do you think that?  What I want to know is how to bridge over a bonded interface?
OK, I went back and looked again, and saw the part I missed as I had not scrolled enough. :)  Try not assigning an IP to the bond0 and only to the br0.  Here is an example without the bond, and you can see my eth1 has no IP.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# Comment out next line to make Network Manager happy
# auto eth1
iface eth1 inet manual

# The bridge interface
auto br0
iface br0 inet dhcp
        bridge_ports eth1
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

```

---

