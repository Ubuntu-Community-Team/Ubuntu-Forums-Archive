---
title: "Server not seeing the network when using static IP"
date: 2012-11-07
forum: Server Platforms
---

### Post by thnewguy on 2012-11-07
I'm running a server at home with Ubuntu Server 12.04 LTS. The server has a static IP address, 192.168.2.25 which is defined, along with a virtual network interface in the /etc/network/interfaces file

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
# iface eth0 inet dhcp
iface eth0 inet static
address 192.168.2.25
netmask 255.255.255.0
broadcast 192.168.2.255
gateway 192.168.2.1


auto virbr0
iface virbr0 inet static
address 192.168.2.40
network 192.168.2.0
netmask 255.255.255.0
broadcast 192.168.2.255
gateway 192.168.2.1
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off

```

This has been working well for the past couple of months and I reboot around once a week, usually to make sure kernel updates applied okay.

Today I rebooted the server and it wasn't able to set up eth0. The server paused during its boot process saying it was "Waiting for network configuration...." Then, a minute later, it displayed. "Waiting up to 60 seconds for network configuration...."
Eventually it booted and brought me to the normal login prompt. However, as far as the server is concerned, eth0 does not exist. The virbr0 interface is there, but eth0 isn't in the list of network interfaces when I run "ifconfig". I have no connection from the server out to the rest of the network.

I found that if I went into /etc/network/interfaces and changed it so that eth0 was set to use DHCP rather than static settings, and rebooted the server, the server properly set up eth0 and came on-line.

My static IP set up has been working for months and I'm not sure why it would suddenly stop. Or, for that matter, why switching to a dynamic IP address fixed the issue. I'd like to get back to a static IP as I use the server for scheduled backups. Any suggestions?

---

