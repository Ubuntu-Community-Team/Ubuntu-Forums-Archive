---
title: "bridging multiple ip's for KVM guests"
date: 2014-03-13
forum: Virtualisation
---

### Post by xeidy on 2014-03-13
Hi, my /etc/network/interfaces looks like this

auto lo
iface lo inet loopback

auto eth0
allow-hotplug eth0
iface eth0 inet static
        address x.x.x.242
        netmask 255.255.255.248
        gateway x.x.x.241
        dns-nameservers x.x.x.1 x.x.x.2

auto eth0:0
allow-hotplug eth0:0
iface eth0:0 inet static
        address x.x.x.243
        netmask 255.255.255.248

auto eth0:1
allow-hotplug eth0:1
iface eth0:1 inet static
        address x.x.x.244
        netmask 255.255.255.248

auto eth0:2
allow-hotplug eth0:2
iface eth0:2 inet static
        address x.x.x.245
        netmask 255.255.255.248

auto eth0:3
allow-hotplug eth0:3
iface eth0:3 inet static
        address x.x.x.246
        netmask 255.255.255.248



what is want is br0, br1, br2, br3 for eth0:0, eth0:1, eth0:2, eth0:3 respectively.

They are on a dedicated server, and I've messed up enough times that i've to create ticket for the host to fix is manually.

Can anyone kindly help me bridging these. I've 5 ips, out of them i want 4 bridge for subsequent KVM vps'es that i am planning to create.

i tried something like this:

auto eth0:0
allow-hotplug eth0:0
iface eth0:0 inet manual

auto br0
iface br0 inet static
        address x.x.x.243
        netmask 255.255.255.248
        gateway x.x.x.241
        bridge_ports eth0:0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off



making such a change made the server stop responding and i had to create a ticket to get it back to original state.

any help would be greatly appreciated. thanks :)

btw, i'm on Ubuntu 12.04

---

### Post by xeidy on 2014-03-13
Anyone with expertise in this matter? Please..

---

### Post by houstonbofh on 2014-03-23
You are doing a lot here all at once...  And the multinetting is interfering with the bridging.  Set up one bridge to eth0, and mutlinet br0 if you must.  But I do not see why you want a lot of bridges all to the same nic.  Bridging is layer2, and multinetting is layer 3.  The bridge does not care about the IP, only the link.

Here is a simple config example...
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# Comment out next line to make Network Manager happy
# auto eth0
iface eth0 inet manual

# The bridge interface
auto br0
iface br0 inet dhcp
        bridge_ports eth1
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

```

---

