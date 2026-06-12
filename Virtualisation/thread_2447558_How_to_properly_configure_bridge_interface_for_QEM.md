---
title: "How to properly configure bridge interface for QEMU + KVM"
date: 2020-07-21
forum: Virtualisation
---

### Post by glorsh66 on 2020-07-21
I want to configure my virtual network in such a way that my virtual machines would be accessible form outside.
In my current configuration I have connection to usual home router to eth0 with DCHP

Right now I have following config in /etc/network/interfaces



```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


auto br0
iface br0 inet static
address 192.168.1.110
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1
bridge_ports eth0
bridge_stp off
bridge_fd 0
bridge_maxwait 0


auto eth0
iface eth0 inet dhcp
allow-hotplug eth0
#iface eth1 inet dhcp
#auto eth2
#allow-hotplug eth2
#iface eth2 inet dhcp
#auto eth3
#allow-hotplug eth3
#iface eth0 inet dhcp

```


It works but sometimes its behavior is really weird - sometimes eth0 gets an IP address from DHCP server (on the router), sometimes I can only access my PC by 192.168.1.110 (br0 interface) 

What is the proper way to configure it?

---

### Post by TheFu on 2020-07-21
Since 17.10, netplan is the way to configure server networking, not the interfaces file.  Use netplan.
netplan.io has examples.

---

