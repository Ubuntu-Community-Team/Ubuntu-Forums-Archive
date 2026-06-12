---
title: "Networking issue with KVM and Two NICs"
date: 2014-01-15
forum: Server Platforms
---

### Post by xrctp1 on 2014-01-15
I have a server with Ubuntu Server 12.04 installed with an Openbox GUI and KVM with two guests. The network configuration is as follows:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
    address 10.0.(vlan).x
    network 10.0.(vlan).0
    netmask 255.255.255.0
    broadcast 10.0.(vlan).255
    gateway 10.0.(vlan).1


auto eth1
iface eth1 inet manual


auto br0
iface br0 inet dhcp
    bridge_ports eth1
    bridge_stp off
    bridge_maxwait 0
    bridge_fd 0

I have been able to get the guests to access the internet and they can ping hosts on the lan. I am unable to ping between guests, between host and guests, and from lan clients to the guests (but can ping the host from the lan). I have pinged from various devices including the switch and have tracked the issue down to the bridge itself. Is there something I am missing in my configuration or some aspect of bridging disallowing this setup? If so is there some way to work around openvswitch being incompatible with compiled kernel modules?

Also: iptables and ebtables have been flushed completely. eth0 hosts a DHCP server which allows clients on the bridge to receive IP addresses.

---

### Post by xrctp1 on 2014-01-15
I have made some progress: by disabling vt-d on both machines (by removing the entries from the .xml files) I am now able to ping out and back in. I still cannot ping between the virtual machines.

---

### Post by nerdtron on 2014-01-16
You have two NIC right?
eth0 is static right? check

eth1 will be the bridge interface right? not quite.

First, if you want your VM to receive DHCP, you don't have to configure dhcp on the bridge interface. It will be better to assign a static IP to the bridge interface like this:
```
auto eth1
iface eth1 inet manual

auto br1
iface br1 inet static
    address 192.168.x.x
    netmask 255.255.255.0
    network 192.168.x.x
    broadcast 192.168.x.x
    gateway 192.168.x.x
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 8.8.8.8 8.8.4.4
    bridge_ports eth1 
    bridge_fd 9 
    bridge_hello 2 
    bridge_maxage 12 
    bridge_stp off


```

Now all you have to do is set the VM NICs as bridged instead of NAT. You can do that using virt-manager for ubuntu. Like this screenshot:
[ATTACH=CONFIG]249525[/ATTACH]

Now if your VMs are set to DHCP mode, they will get an IP from your DHCP server through the bridge interface. You will be able to ping VM to VM and any server on your LAN.

---

### Post by xrctp1 on 2014-01-21
After several hours of fighting with it and trying that configuration I was still unsuccessful. I have since performed a clean install of Ubuntu 13.10 in hopes that openvswitch will be compatible.

---

### Post by xrctp1 on 2014-01-23
I figured out a way to make it work. I highly doubt this is a proper configuration in any sense of the term but I setup a bridge for each VM in openvswitch and connected them as direct devices.

---

