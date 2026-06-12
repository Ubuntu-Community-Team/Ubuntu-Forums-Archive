---
title: "Centos 7 pptp(ppp0) on openvpn"
date: 2018-03-16
forum: Ubuntu/Debian BASED
---

### Post by superlep on 2018-03-16
Good morning I have a problem that does not solve to solve:

I have a vps in which is installed openvpn server to which I am  connected with my home pc and through which I browse (openvpn client).

the server is a centos 7 while the client is a debian.

I needed a pptp connection on another network, which I did on the server, and it works from the server.

I have a ppp0 on the server and if I ping the computers on the other network it works.

But now I wanted to work with my Debian client on the ppp0  network create , so I needed to redirect ppp0 on vpn and that's where I  panicked.

This is the result of my route -n:

```
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 10.0.0.1 0.0.0.0 UG 0 0 0 eth0
10.0.0.1 0.0.0.0 255.255.255.255 UH 0 0 0 eth0
10.0.1.1 0.0.0.0 255.255.255.255 UH 0 0 0 ppp0
10.8.0.0 10.8.0.2 255.255.255.0 UG 0 0 0 tun0
10.8.0.2 0.0.0.0 255.255.255.255 UH 0 0 0 tun0
141.111.111.111 10.0.0.1 255.255.255.255 UGH 0 0 0 eth0
169.254.0.0 0.0.0.0 255.255.0.0 U 1002 0 0 eth0
172.27.224.0 0.0.0.0 255.255.252.0 U 0 0 0 as0t0
172.27.228.0 0.0.0.0 255.255.252.0 U 0 0 0 as0t1
172.27.232.0 0.0.0.0 255.255.252.0 U 0 0 0 as0t2
172.27.236.0 0.0.0.0 255.255.252.0 U 0 0 0 as0t3
```

of course I changed, for privacy, the WAN IP of the remote server (141.111.111.111) of the ppp0 network

And this is my ifconfig where I changed , for privacy, the WAN IP (119.119.22.234) of the vps server

```
as0t0: flags = 4305 <UP, POINTOPOINT, RUNNING, NOARP, MULTICAST> mtu 1500
inet 172.27.224.1 netmask 255.255.252.0 destination 172.27.224.1
inet6 fe80 :: 9708: 31a1: b4da: 661b prefixlen 64 scopeid 0x20 <link>
unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00 txqueuelen 200 (UNSPEC)
RX packets 0 bytes 0 (0.0 B)
RX errors 0 dropped 0 overruns 0 frames 0
TX packets 3 bytes 144 (144.0 B)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0

as0t1: flags = 4305 <UP, POINTOPOINT, RUNNING, NOARP, MULTICAST> mtu 1500
inet 172.27.228.1 netmask 255.255.252.0 destination 172.27.228.1
inet6 fe80 :: d0a0: 814b: a640: 22d7 prefixlen 64 scopeid 0x20 <link>
unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00 txqueuelen 200 (UNSPEC)
RX packets 0 bytes 0 (0.0 B)
RX errors 0 dropped 0 overruns 0 frames 0
TX packets 3 bytes 144 (144.0 B)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0

as0t2: flags = 4305 <UP, POINTOPOINT, RUNNING, NOARP, MULTICAST> mtu 1500
inet 172.27.232.1 netmask 255.255.252.0 destination 172.27.232.1
inet6 fe80 :: e535: 67c1: 1b56: 46af prefixlen 64 scopeid 0x20 <link>
unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00 txqueuelen 200 (UNSPEC)
RX packets 341340 bytes 40795619 (38.9 MiB)
RX errors 0 dropped 0 overruns 0 frames 0
TX packets 376479 bytes 338875121 (323.1 MiB)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0

as0t3: flags = 4305 <UP, POINTOPOINT, RUNNING, NOARP, MULTICAST> mtu 1500
inet 172.27.236.1 netmask 255.255.252.0 destination 172.27.236.1
inet6 fe80 :: d5c8: 5d90: c362: 5741 prefixlen 64 scopeid 0x20 <link>
unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00 txqueuelen 200 (UNSPEC)
RX packets 75509 bytes 8301516 (7.9 MiB)
RX errors 0 dropped 0 overruns 0 frames 0
TX packets 78776 bytes 53650147 (51.1 MiB)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0

eth0: flags = 4163 <UP, BROADCAST, RUNNING, MULTICAST> mtu 1500
inet 119.119.22.234 netmask 255.255.255.255 broadcast 119.119.22.234
inet6 fe80 :: xxxxxxxxxxxxxxxxx prefixlen 64 scopeid 0x20 <link>
ether 52: xxxxxxxxxxxxxxxxx txqueuelen 1000 (Ethernet)
RX packets 28057906 bytes 6206153016 (5.7 GiB)
RX errors 0 dropped 0 overruns 0 frames 0
TX packets 15287842 bytes 6761961483 (6.2 GiB)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0

lo: flags = 73 <UP, LOOPBACK, RUNNING> mtu 65536
inet 127.0.0.1 netmask 255.0.0.0
inet6 :: 1 prefixlen 128 scopeid 0x10 <host>
loop txqueuelen 1 (Local Loopback)
RX packets 26555 bytes 7344517 (7.0 MiB)
RX errors 0 dropped 0 overruns 0 frames 0
TX packets 26555 bytes 7344517 (7.0 MiB)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0

ppp0: flags = 4305 <UP, POINTOPOINT, RUNNING, NOARP, MULTICAST> mtu 1446
inet 10.0.0.240 netmask 255.255.255.255 destination 10.0.1.1
ppp txqueuelen 3 (Point-to-Point Protocol)
RX packets 8 bytes 74 (74.0 B)
RX errors 0 dropped 0 overruns 0 frames 0
TX packets 7 bytes 70 (70.0 B)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0

tun0: flags = 4305 <UP, POINTOPOINT, RUNNING, NOARP, MULTICAST> mtu 1500
inet 10.8.0.1 netmask 255.255.255.255 destination 10.8.0.2
inet6 xxxxxxxxxxxxxxxxxxxc prefixlen 64 scopeid 0x20 <link>
unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00 txqueuelen 100 (UNSPEC)
RX packets 0 bytes 0 (0.0 B)
RX errors 0 dropped 0 overruns 0 frames 0
TX packets 71 bytes 7368 (7.1 KiB)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0
```

what ip route or iptables commands should I give to show both networks on my Debian client? Thank you.

---

### Post by jeremy31 on 2018-03-16
*Thread moved to **Ubuntu/Debian BASED**.*

---

