---
title: "KVM Bridge Problem"
date: 2012-03-10
forum: Virtualisation
---

### Post by flyshoo on 2012-03-10
Hello, I have an issue with the bridge config on my host server.  I'm using Ubuntu Server 10.04.04 with kvm, guest Win2K8 R2.  I configured the a bridge in /etc/network/interfaces/ br0 but the host lost connectivity.  When I run ifconfig an interface vnet0 shows up.  I didn't configure vnet0 and I can't find where it is configured.  I looked in the guest config file and didn't find an entry for vnet0 but br0 is configured.  Also I looked for the network interface in the guest details in virt-manager, no entry.  I can't find the config file for vnet0 and I don't know how to disable it.  Can someone help me understand the issue and how to resolve it?

This is my config for the network interfaces:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 10.22.33.130
	netmask 255.255.255.0
	gateway 10.22.33.3

# The secondary network interface for bridge
auto eth1
iface eth1 inet manual

# The VM network bridge
auto br0
iface br0 inet manual
	bridge_ports eth1
	bridge_stp yes
	bridge_fd 0
	bridge_maxwait 0

Thank you.
flyshoo

---

