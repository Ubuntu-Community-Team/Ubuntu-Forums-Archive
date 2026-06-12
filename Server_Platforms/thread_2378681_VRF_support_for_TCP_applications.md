---
title: "VRF support for TCP applications"
date: 2017-11-25
forum: Server Platforms
---

### Post by jimraynor2 on 2017-11-25
I have an Ubuntu 16.04.3 Server, with the default kernel (4.4.0-87-generic) coming with this release. This Ubuntu machine has four network interfaces (eth0 - eth3) and its eth2 interface is connected to a server in the network, which serves from tcp 8080 port. I am trying to setup VRF on my Ubuntu machine and adding eth2 interface to this VRF.

Ubuntu eth2 IP: 192.168.120.134
Server IP: 192.168.120.124

After my VRF configuration, I am able to ping the Server from Ubuntu with: "ping -I eth2 192.168.120.124 -c4". I verified it with tcpdump trace taken on both Ubuntu and the Server. However when I try to connect to 192.168.120.124:8080 via a Client application from Ubuntu the three-way-handshake is not being completed. Interesting part is my machine is able to send the SYN packet from the eth2 interface, receives the SYN-ACK response from the server, however sending a Reset packet back to the server.

**Ping Test**
```
ping -I eth2 192.168.120.124 -c4
PING 192.168.120.124 (192.168.120.124) from 192.168.120.134 eth2: 56(84) bytes of data.
64 bytes from 192.168.120.124: icmp_seq=1 ttl=64 time=0.794 ms
64 bytes from 192.168.120.124: icmp_seq=2 ttl=64 time=0.333 ms
64 bytes from 192.168.120.124: icmp_seq=3 ttl=64 time=0.365 ms
64 bytes from 192.168.120.124: icmp_seq=4 ttl=64 time=0.352 ms
```

```
tcpdump -ni eth2 host 192.168.120.124
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth2, link-type EN10MB (Ethernet), capture size 262144 bytes


21:18:57.507749 IP 192.168.120.134 > 192.168.120.124: ICMP echo request, id 1769, seq 1, length 64
21:18:57.508518 IP 192.168.120.124 > 192.168.120.134: ICMP echo reply, id 1769, seq 1, length 64
21:18:58.508617 IP 192.168.120.134 > 192.168.120.124: ICMP echo request, id 1769, seq 2, length 64
21:18:58.508905 IP 192.168.120.124 > 192.168.120.134: ICMP echo reply, id 1769, seq 2, length 64
21:18:59.508662 IP 192.168.120.134 > 192.168.120.124: ICMP echo request, id 1769, seq 3, length 64
21:18:59.508981 IP 192.168.120.124 > 192.168.120.134: ICMP echo reply, id 1769, seq 3, length 64
21:19:00.508657 IP 192.168.120.134 > 192.168.120.124: ICMP echo request, id 1769, seq 4, length 64
21:19:00.508935 IP 192.168.120.124 > 192.168.120.134: ICMP echo reply, id 1769, seq 4, length 64
```

**TCP Connection Test**
```
./Client1 eth2 192.168.120.124 8080
```

```
21:23:46.621832 IP 192.168.120.134.36270 > 192.168.120.124.8080: Flags [S], seq 3039224924, win 29200, options [mss 1460,sackOK,TS val 208048 ecr 0,nop,wscale 7], length 0
21:23:46.622181 IP 192.168.120.124.8080 > 192.168.120.134.36270: Flags [S.], seq 538319858, ack 3039224925, win 28960, options [mss 1460,sackOK,TS val 828394395 ecr 208048,nop,wscale 5], length 0
21:23:46.622237 IP 192.168.120.134.36270 > 192.168.120.124.8080: Flags [R], seq 3039224925, win 0, length 0
21:23:47.620565 IP 192.168.120.134.36270 > 192.168.120.124.8080: Flags [S], seq 3039224924, win 29200, options [mss 1460,sackOK,TS val 208298 ecr 0,nop,wscale 7], length 0
21:23:47.620926 IP 192.168.120.124.8080 > 192.168.120.134.36270: Flags [S.], seq 553924926, ack 3039224925, win 28960, options [mss 1460,sackOK,TS val 828394645 ecr 208298,nop,wscale 5], length 0
21:23:47.620977 IP 192.168.120.134.36270 > 192.168.120.124.8080: Flags [R], seq 3039224925, win 0, length 0
21:23:49.624560 IP 192.168.120.134.36270 > 192.168.120.124.8080: Flags [S], seq 3039224924, win 29200, options [mss 1460,sackOK,TS val 208799 ecr 0,nop,wscale 7], length 0
21:23:49.624969 IP 192.168.120.124.8080 > 192.168.120.134.36270: Flags [S.], seq 585237744, ack 3039224925, win 28960, options [mss 1460,sackOK,TS val 828395146 ecr 208799,nop,wscale 5], length 0
21:23:49.625013 IP 192.168.120.134.36270 > 192.168.120.124.8080: Flags [R], seq 3039224925, win 0, length 0
```


Meanwhile the three-way-handshake attempt, on another terminal, the netstat utility shows that the socket is created as expected like below:

```
netstat -tupan | grep 8080
tcp        0      1 192.168.120.134:36270   192.168.120.124:8080    SYN_SENT    1849/Client1
```

I am not an expert on this, trying to implement VRF with the help of the information that I found on internet. The interesting part seems the received SYN-ACK packet is somehow not being associated with the existing socket for this connection, so the socket stays in the SYN-SENT state. I am wondering if I missed something on my configuration, and it would be appreciated to hear your suggestions.

**Configuration for VRF**

ip link add client type vrf table 1
ip link set dev client up

ip link set eth2 master client

ip rule add iif client table 1
ip rule add oif client table 1
ip rule add iif eth2 table 1
ip rule add oif eth2 table 1

ip route add 0.0.0.0/0 via 192.168.120.124 table 1


It shows the vrf status as UNKNOWN, can this be the problem? However ICMP works.
```
ip -br link show type vrf
client           UNKNOWN        2a:a7:08:fc:83:d3 <NOARP,MASTER,UP,LOWER_UP>
```

```
ip link show eth2
4: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master client state UP mode DEFAULT group default qlen 1000
    link/ether 00:50:56:82:7a:80 brd ff:ff:ff:ff:ff:ff
```

```
ip route show table 1
default via 192.168.120.124 dev eth2
broadcast 192.168.120.0 dev eth2  proto kernel  scope link  src 192.168.120.134
192.168.120.0/24 dev eth2  proto kernel  scope link  src 192.168.120.134
local 192.168.120.134 dev eth2  proto kernel  scope host  src 192.168.120.134
broadcast 192.168.120.255 dev eth2  proto kernel  scope link  src 192.168.120.134
```

arp and ip neighbor tables right after the test:
```
arp -an
? (192.168.120.124) at fc:15:b4:09:2d:81 [ether] on eth2
? (172.16.0.141) at 00:50:56:82:6d:40 [ether] on eth0
? (192.168.120.2) at 00:01:d7:a7:72:44 [ether] on eth2
? (192.168.126.1) at 00:01:d7:a7:72:46 [ether] on eth3
```

```
ip neighbor
192.168.120.124 dev eth2 lladdr fc:15:b4:09:2d:81 REACHABLE
172.16.0.141 dev eth0 lladdr 00:50:56:82:6d:40 REACHABLE
192.168.120.2 dev eth2 lladdr 00:01:d7:a7:72:44 STALE
192.168.126.1 dev eth3 lladdr 00:01:d7:a7:72:46 STALE
```

Thanks in advance for your suggestions

---

### Post by DuckHook on 2017-11-25
Welcome to the forums, jimraynor2.

Please don't duplicate post into different subforums. It confuses those trying to help and dilutes community effort. I've removed your other thread from public view.

Thanks.

---

### Post by iwanyu on 2018-07-13
Hi, jimraynor2:

The command "**sysctl -w net.ipv4.tcp_l3mdev_accept=1**" may help you solve the problem. The reason is that your serves from TCP 8080 port only take effect on the default VRF by default, and the TCP services running in the default VRF context (ie., not bound to any VRF device) can work across all VRF domains by enabling the tcp_l3mdev_acceptsysctl options.

best regards.

---

