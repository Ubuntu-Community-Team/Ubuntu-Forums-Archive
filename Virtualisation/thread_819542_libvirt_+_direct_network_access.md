---
title: "libvirt + direct network access"
date: 2008-06-05
forum: Virtualisation
---

### Post by seabra on 2008-06-05
Hello

 I installed libvirt on ubuntu 8.04 server.
 I have a virtual machine running WindowsXP and almost everything is working fine.
 My problem is that I need WindowsXP to access network directly.
 With this I mean that i need WindowsXP to get an IP from the DHCP server in the LAN and not some sort of NAT/route.
 I have read the documentation but i can only find route/nat solutions and this is not what i need.
 Is there a way to do this?

S

---

### Post by ktulu73 on 2008-06-07
You have to setup bridged network for you host.
Install bridge utils
```
sudo aptitude install bridge-utils
```

To configure bridge support for your network, you have to edit /etc/network/interfaces like this example:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static

#iface eth0 inet static
#address 192.168.2.190
#netmask 255.255.255.0
#gateway 192.168.2.1

# The bridge network interface(s)
auto br0
iface br0 inet static
address 192.168.2.190
network 192.168.2.0
netmask 255.255.255.0
broadcast 192.168.2.255
gateway 192.168.2.1
dns-nameservers 192.168.2.1
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off

```

With that your host has a static ip 192.168.2.190. If you need also dhcp on your host, please try that:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static

#iface eth0 inet static
#address 192.168.2.190
#netmask 255.255.255.0
#gateway 192.168.2.1

# The bridge network interface(s)
auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off

```

Then you have to enable the bridge for your Windows guest in libvirt's (guest) xml:

```
<interface type='bridge'>
      <mac address='52:54:00:32:25:39'/>
      <source bridge='br0'/>
    </interface>
```

After that, restart libvirt.

---

