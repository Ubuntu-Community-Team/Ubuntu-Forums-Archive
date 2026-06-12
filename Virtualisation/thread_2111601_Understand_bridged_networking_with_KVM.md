---
title: "Understand bridged networking with KVM"
date: 2013-02-02
forum: Virtualisation
---

### Post by Erik-NA on 2013-02-02
I am a KVM-newbee and have a question about KVM and bridged networking for Ubuntu 12.04.

I am investigating how to setup a virtualized firewall, [Sophos UTM 9]("http://www.sophos.com/en-us/products/free-tools/sophos-utm-home-edition.aspx") and has not fully understand how to configure the KVM-host bridged networking.

The KVM-host has three phsyical NICS:

[LIST]
[*]Internal - eth0
[*]Wireless - eth1
[*]External - eth2
[/LIST]

**Internal network**
Network: 192.168.1.0/24
GW: 192.168.1.1 (UTM9 NIC IP-adress)

UTM9 is both DHCP-server and gateway for the Internal Network, has the static IP-adress 192.168.1.1. The KVM-host has a static IP-address on this network, 192.168.1.250

**Wireless network**
Network: 192.168.4.0/24
GW: 192.168.4.1 (UTM9 NIC IP-adress)

UTM9 is both DHCP-server and gateway for the Wireless Network, has the static IP-address 192.168.4.1
The KVM-host shall not have IP-connectivity on this network.

**External network**
Network 147.13.10.0/25
GW: 147.13.10.1 (ISP gateway)

UTM9 has a static IP-adresses on External, 147.13.10.2.
The KVM-host shall not have IP-connectivity on this network.

My question is how I shall setup bridged networking on the KVM-host? Can anyone give me an example how to configure /etc/networking/interfaces with bridged networking on the KVM-host according to above?



Cheers

---

### Post by Erik-NA on 2013-02-03
I have done some progress.

/etc/network/interfaces is now configured as followed:

```
# The loopback network interface
auto lo
iface lo inet loopback

#Internal network
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 192.168.1.250
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        dns-nameservers 192.168.1.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

#Wireless network
auto eth1
iface eth1 inet manual

auto br1
iface br1 inet static
        bridge_ports eth1
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

#External network
auto eth2
iface eth2 inet manual

auto br2
iface br2 inet static
        bridge_ports eth2
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```

When I restart networking I am getting the following errors:

Br1:
Missing required variable: address
Missing required configuration variables for interface br1/inet.

Br2:
Missing required variable: address
Missing required configuration variables for interface br2/inet.

The problem is that I do not want the KVM-host to have networking on eth1 and eth2. However, the virtual instance should have networking on these two physical interfaces.

How do I fix this?

---

### Post by Erik-NA on 2013-02-03
I am reading [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking) and it seems that when using bridged networking, virtual guests are accessing the network using the KVM-hosts IP address?

I want go give my VM guest their own IPs, which is described in the "IP Aliases" chapter. But I do not want the KVM-host to have IP-connectivity on eth1 and eth2. How do I solve that?

---

### Post by Erik-NA on 2013-02-04
This seems to work. 

```

# The loopback network interface
auto lo
iface lo inet loopback

#Internal network
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
	address 192.168.1.250
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        dns-nameservers 192.168.1.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

#Wireless network
auto eth1
iface eth1 inet manual

auto br1
iface br1 inet static
        address 0.0.0.0
        bridge_ports eth1
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

#External network
auto eth2
iface eth2 inet manual

auto br2
iface br2 inet static
        address 0.0.0.0
        bridge_ports eth2
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

```

---

### Post by Erik-NA on 2013-02-05
False response, the networking is not functional on br1 and br2 :(

I am starting to believe that it is impossible to deny IP-connectivity for the KVM-host on a bridged (physical) interface?

---

