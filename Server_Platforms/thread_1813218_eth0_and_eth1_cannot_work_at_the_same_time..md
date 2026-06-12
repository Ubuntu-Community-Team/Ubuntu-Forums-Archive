---
title: "eth0 and eth1 cannot work at the same time."
date: 2011-07-27
forum: Server Platforms
---

### Post by NetDoc on 2011-07-27
I have two ethernet ports on my SuperMicro server. When I start the system, only eth1 is operable. If I ifup eth0, I get a message that it is already configured, but I can't ping any of the IPs on it.

If I ifdown eth1, then ifdown eth0 and ifup eth0, then I can ping any of the IPs on eth0 in the interfaces file. Of course, now eth1 is not reachable. 

```
root@epsilon:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:48:35:2a:32  
          inet addr:209.208.24.242  Bcast:209.208.24.255  Mask:255.255.255.240
          inet6 addr: fe80::230:48ff:fe35:2a32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:703 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:921011 (921.0 KB)  TX bytes:68920 (68.9 KB)
          Memory:da000000-da020000 

eth0:1    Link encap:Ethernet  HWaddr 00:30:48:35:2a:32  
          inet addr:209.208.24.244  Bcast:209.208.24.255  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Memory:da000000-da020000 

eth0:2    Link encap:Ethernet  HWaddr 00:30:48:35:2a:32  
          inet addr:209.208.24.246  Bcast:209.208.24.255  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Memory:da000000-da020000 

eth0:3    Link encap:Ethernet  HWaddr 00:30:48:35:2a:32  
          inet addr:209.208.24.248  Bcast:209.208.24.255  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Memory:da000000-da020000 

eth0:4    Link encap:Ethernet  HWaddr 00:30:48:35:2a:32  
          inet addr:209.208.24.250  Bcast:209.208.24.255  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Memory:da000000-da020000 

eth0:5    Link encap:Ethernet  HWaddr 00:30:48:35:2a:32  
          inet addr:209.208.24.252  Bcast:209.208.24.255  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Memory:da000000-da020000 

eth0:6    Link encap:Ethernet  HWaddr 00:30:48:35:2a:32  
          inet addr:209.208.24.254  Bcast:209.208.24.255  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Memory:da000000-da020000 

eth0:7    Link encap:Ethernet  HWaddr 00:30:48:35:2a:32  
          inet addr:192.168.2.120  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Memory:da000000-da020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:197 errors:0 dropped:0 overruns:0 frame:0
          TX packets:197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20787 (20.7 KB)  TX bytes:20787 (20.7 KB)

```

```
  GNU nano 2.2.2                                  File: /etc/network/interfaces                                                                            

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0 eth0:1 eth0:2 eth0:3 eth0:4 eth0:5 eth0:6 eth0:7 eth1 eth1:1 eth1:2 eth1:3 eth1:4 eth1:5
iface eth0 inet static
        address 209.208.24.242
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
        gateway 209.208.24.241
iface eth0:1 inet static
        address 209.208.24.244
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface eth0:2 inet static
        address 209.208.24.246
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface eth0:3 inet static
        address 209.208.24.248
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface eth0:4 inet static
        address 209.208.24.250
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface eth0:5 inet static
        address 209.208.24.252
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface eth0:6 inet static
        address 209.208.24.254
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface eth0:7 inet static
        address 192.168.2.120
        netmask 255.255.255.0
        network 192.168.2.1
        broadcast 192.168.2.255
iface eth1 inet static
        address 209.208.24.243
        netmask 255.255.255.240
        broadcast 209.208.24.255
        gateway 209.208.24.241
iface eth1:1 inet static
        address 209.208.24.245
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface eth1:2 inet static
        address 209.208.24.247
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface eth1:3 inet static
        address 209.208.24.249
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface eth1:4 inet static
        address 209.208.24.251
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface eth1:5 inet static
        address 209.208.24.253
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255

```

---

### Post by karlson on 2011-07-27
> **NetDoc said:**
> I have two ethernet ports on my SuperMicro server. When I start the system, only eth1 is operable. If I ifup eth0, I get a message that it is already configured, but I can't ping any of the IPs on it.

If I ifdown eth1, then ifdown eth0 and ifup eth0, then I can ping any of the IPs on eth0 in the interfaces file. Of course, now eth1 is not reachable. 


Have you tried configuring bonding?

---

### Post by Wayne_V on 2011-07-27
so am I reading this then that all the IPs on both NICs are on the same subnet:


sipcalc 209.208.24.242/28
-[ipv4 : 209.208.24.242/28] - 0

[CIDR]
Host address		- 209.208.24.242
Host address (decimal)	- 3520076018
Host address (hex)	- D1D018F2
Network address		- 209.208.24.240
Network mask		- 255.255.255.240
Network mask (bits)	- 28
Network mask (hex)	- FFFFFFF0
Broadcast address	- 209.208.24.255
Cisco wildcard		- 0.0.0.15
Addresses in network	- 16
Network range		- 209.208.24.240 - 209.208.24.255
Usable range		- 209.208.24.241 - 209.208.24.254


So if both NICs are up you probably will only have access to one of them given that the system will be trying to route traffic for that subnet on only one NIC (probably the last one up'd).

Check the route tables when you are doing this.  Or better yet, move them to different subnets.

---

### Post by bakegoodz on 2011-07-28
Networking in Linux sometimes makes assumptions. I have often seen Linux assume that using more than one interface you probably want have the kernel doing routing between them. It won't assume that if you bridge the connections, basic make your computer a switch. I don't understand what your trying to accomplish spreading many sub interfaces across two physical interfaces all using the same subnet. Not sure this will help you, but here you go.

apt-get install bridge-utils

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto br0:1 br0:2 br0:3 br0:4 br0:5 br0:6 br0:7 br0:8 br0:9 br0:10 br0:11 br0:12 br0:13
iface br0 inet static
  address 209.208.24.242
  netmask 255.255.255.240
  network 209.208.24.240
  broadcast 209.208.24.255
  gateway 209.208.24.241
  pre-up ifconfig eth0 down
  pre-up ifconfig eth1 down
  pre-up brctl addbr br0
  pre-up brctl addif br0 eth0 eth1 
  pre-up ifconfig eth0 up
  pre-up ifconfig eth1 up
  post-down ifconfig eth0 down
  post-down ifconfig eth1 down
  post-down brctl delif br0 eth0 eth1

iface br0:1 inet static
        address 209.208.24.244
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface br0:2 inet static
        address 209.208.24.246
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface br0:3 inet static
        address 209.208.24.248
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface br0:4 inet static
        address 209.208.24.250
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface br0:5 inet static
        address 209.208.24.252
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface br0:6 inet static
        address 209.208.24.254
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface br0:7 inet static
        address 192.168.2.120
        netmask 255.255.255.0
        network 192.168.2.1
        broadcast 192.168.2.255
iface br0:8 inet static
        address 209.208.24.243
        netmask 255.255.255.240
        broadcast 209.208.24.255
        gateway 209.208.24.241
iface br0:9 inet static
        address 209.208.24.245
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface br0:10 inet static
        address 209.208.24.247
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface br0:11 inet static
        address 209.208.24.249
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface br0:12 inet static
        address 209.208.24.251
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface br0:13 inet static
        address 209.208.24.253
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255

---

### Post by NetDoc on 2011-07-28
Thanks for the replies. The solution was incredibly simple. 

I removed the gateway statement from eth1. 

It all works flawlessly now. As for the multihoned interfaces... this is a LAMP server and will be hosting some domains with dedicated IPs. 

> **NetDoc said:**
> I have two ethernet ports on my SuperMicro server. When I start the system, only eth1 is operable. If I ifup eth0, I get a message that it is already configured, but I can't ping any of the IPs on it.

If I ifdown eth1, then ifdown eth0 and ifup eth0, then I can ping any of the IPs on eth0 in the interfaces file. Of course, now eth1 is not reachable. 

---

