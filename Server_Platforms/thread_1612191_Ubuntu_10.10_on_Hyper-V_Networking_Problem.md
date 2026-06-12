---
title: "Ubuntu 10.10 on Hyper-V Networking Problem"
date: 2010-11-02
forum: Server Platforms
---

### Post by Zarrin on 2010-11-02
Hello, I am having some problems with networking on Ubuntu 10.10 running as a guest os on Hyper-V 2008. I am running Windows Server 2008 R2 as the host os. What I am trying to do is run openVPN on the Ubuntu server to use it as for external access to the network. I did have a Ubuntu 10.04 server running before as a separate box, but when I put the windows server in, I wanted to mess with Hyper-V and the Ubuntu server was a good candidate to virtualise.

As I have it now, I am able to connect to the VPN, but no traffic will pass from the VPN to the internal network. I have IPv4 forwarding enabled, and tested by setting a separate computer to use the ubuntu server as a default gateway. I currently have it set as an ethernet bridge, which is prefered because i also use the VPN for games from time to time. From the ubuntu server, i can ping hosts on the internal network and the VPN.

My /etc/network/interfaces:
iface lo inet loopback

# The primary network interface
iface br0 inet static
        address 192.168.42.3
        netmask 255.255.255.0
        network 192.168.42.0
        broadcast 192.168.42.255
        gateway 192.168.42.1
        bridge_ports eth3 tap0

Output from ifconfig:

br0       Link encap:Ethernet  HWaddr 00:15:5d:2a:15:00
          inet addr:192.168.42.3  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::215:5dff:fe2a:1500/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2854733 (2.8 MB)  TX bytes:417555 (417.5 KB)

eth3      Link encap:Ethernet  HWaddr 00:15:5d:2a:15:00
          inet6 addr: fe80::215:5dff:fe2a:1500/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39932 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7865367 (7.8 MB)  TX bytes:465289 (465.2 KB)
          Interrupt:9 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap0      Link encap:Ethernet  HWaddr ce:92:ef:42:1b:12
          inet6 addr: fe80::cc92:efff:fe42:1b12/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23893 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:5444 (5.4 KB)  TX bytes:2933533 (2.9 MB)

I have run out of ideas of what this could be, please help.

---

