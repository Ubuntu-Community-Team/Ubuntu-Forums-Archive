---
title: "network connection fails upon configuring a bridge"
date: 2011-03-19
forum: Server Platforms
---

### Post by KarelV on 2011-03-19
I have a Ubuntu 10.10 server running and a virtual machine installed, also based on Ubuntu 10.10.
As soon as I configure a bridge to connect the virtual machine, I cannot access the server from the network any more.

At first, without bridge on the host, I have internet access and I can remote login and can access Samba shares. My configuration is then:
```
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

#auto br1
#iface br1 inet dhcp
#        bridge_ports eth0
#        bridge_stp off
#        bridge_fd 0
#        bridge_maxwait 0
```

When I include the bridge, as in the lines that are commented out, after some time or after rebooting, I loose access of all services at the server host.

When I also change the eth0 port of the bridge to a second NIC: eth1, then I also loose my internet connection.

I tried static configuration of the bridge according many examples, but without result.

I have the feeling that I have to change the routing, but do not know how.
This is my routing without bridge:```
ip route show
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.22
192.168.122.0/24 dev virbr0  proto kernel  scope link  src 192.168.122.1
default via 192.168.1.2 dev eth0  metric 100
```

This is my routing with bridge:```
ip route show
192.168.1.0/24 dev br1  proto kernel  scope link  src 192.168.1.22
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.22
192.168.122.0/24 dev virbr0  proto kernel  scope link  src 192.168.122.1
default via 192.168.1.2 dev eth0  metric 100
default via 192.168.1.2 dev br1  metric 100
```

Where do I have to look for?

---

### Post by KarelV on 2011-03-22
Trying to solve my problem, as described in my first posting, some questions arise.

When I remove the bridge interface and restart networking, | have access to my server-host immediately. When I include the bridge interface and restart networking. I will keep access for some time before it disappears or until I reboot.
my first question: what can be changed on the network configuration after some time or at reboot which is not changed on restarting networking in this second situation?

When I included the bridge br1 at first, also an interface called virbr0 is shown. While br1 gets the same IP as eth0, virbr0 gets 192.168.122.1/24. This means that it does not listen to the dhcp server in my network, because my network is defined by 192.168.1.0/24. virbr0 is not defined in /etc/network/interfaces and it is not removed when I remove the first bridge br1.
My second question: Do I need this additional bridge and what is the reason for a new subnet?

---

### Post by Cheesehead on 2011-03-22
VirtualBox or Vmware? It makes a small difference.

As you have already figured out, the *host* does not need any kind of bridge. It is already available and accessable.

The *guest* uses pseudo-'bridge' networking instead of NAT in order to get it's own separate IP address from your router/gateway. But in VirtualBox (for example), 100% of that configuration is done within VB. Don't mess with *host* networking!

A real bridge is used to join two subnets, so they seem to be just one. For example, a home wireless router has three interfaces: Internet, Wired LAN, Wireless LAN. The two LANs are usually Bridged so users see a single wired+wireless 'LAN'. That way, a wireless laptop can 'see' a wired printer even though they are on two different subnets separated by a router. Bridging makes the router transparent (a Bridge) in this case.

---

### Post by KarelV on 2011-03-23
I understand from you, that it depends on the hypervisor used, in my case KVM-libvirt.
In my case the connectivity is then configured as follows:
First, I configured a switch br1 in the host with one fysical interface. This switch gets the same address as the physical interface. This bridge is transparent for addresses of my local network. Secondly, I defined a virtual machine with the bridge br1 for networking. KVM-libvirt configured then a second bridge, virbr0, without fysical interface and the address 192.168.122.1. This switch does address translation. Third, I installed an OS on the virtual machine. That OS finds a virtual interface eth0, that gets the address 192.168.122.34 and gateway 192.168.122.1.
From the local network, the address of virbr0 must the address to reach the virtual machine, which is translated to 192.168.122.34. Furthermore, I think that a static interface in the virtual machine does not work, because I have no means to configure the address translation.

Please correct me if I'm wrong.

I hope someone can also answer my first question on the difference in network configuration between /etc/init.d/networking restart and rebooting.

---

### Post by KarelV on 2011-03-23
The problem is solved.
The correct configuration of interfaces is:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

auto br1
iface br1 inet dhcp
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
```
I solved the problem by commenting out the eth0 configuration as explained on:
[http://www.linux-kvm.org/page/Networking](http://www.linux-kvm.org/page/Networking)

---

