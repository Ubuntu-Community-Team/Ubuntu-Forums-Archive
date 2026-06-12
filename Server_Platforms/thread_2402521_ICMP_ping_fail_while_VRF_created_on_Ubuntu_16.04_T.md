---
title: "ICMP ping fail while VRF created on Ubuntu 16.04 TL"
date: 2018-10-01
forum: Server Platforms
---

### Post by syang2466 on 2018-10-01
I tried to create VRF on Ubuntu 16.04 TLS, and I target to build BGP vrf and OSPF vrf on FRR for multi-tenants over single server host if VRF is successful.
However the ICMP ping over linux vrf enabled interface is not successful. I am looking for the help to investigate this problem.


The setup process:
Environment: 
Host A (ubuntu) lan2 10.11.0.2/30---direct connect---10.11.0.1/30 (vrf blue) lan2 Host B (EC-2)
Host A use local routing table by default; Host B created vrf blue in the following:

```
root@Sam-EC2:~# ip link add name blue type vrf table 10
root@Sam-EC2:~# ip link set dev blue up
root@Sam-EC2:~# ip -br link show type vrf
blue             UP             42:ea:40:25:1b:85 <NOARP,MASTER,UP,LOWER_UP> 
root@Sam-EC2:~# ip route add table 10 unreachable default
root@Sam-EC2:~# ip link set dev lan2 master blue
root@Sam-EC2:~# ip address add 10.11.0.1/30 dev lan2

root@Sam-EC2:~# ip rule add iif blue table 1
root@Sam-EC2:~# ip rule add oif blue table 1
```
```
root@Sam-EC2:~# ip rule show
98:     from all oif blue lookup 10 
99:     from all iif blue lookup 10 
100:    from all lookup local 
110:    from all lookup 10021 
220:    from all lookup 220 
1000:   from all 
32765:  from all lookup 10021 
32766:  from all lookup main 
32767:  from all lookup default 

```
```
root@Sam-EC2:~# ip route show table 10 dev lan2
#Note. Routing Table 10 looks good.
broadcast 10.11.0.0  proto kernel  scope link  src 10.11.0.1 
10.11.0.0/30  proto kernel  scope link  src 10.11.0.1 
local 10.11.0.1  proto kernel  scope host  src 10.11.0.1 
broadcast 10.11.0.3  proto kernel  scope link  src 10.11.0.1 

```
```
root@Sam-EC2:~# ping 10.11.0.1 -I lan2
#note. this is ping lan2 itself on host (EC-2)
PING 10.11.0.1 (10.11.0.1) from 10.11.0.1 lan2: 56(84) bytes of data.
64 bytes from 10.11.0.1: icmp_seq=1 ttl=64 time=0.114 ms
64 bytes from 10.11.0.1: icmp_seq=2 ttl=64 time=0.092 ms
64 bytes from 10.11.0.1: icmp_seq=3 ttl=64 time=0.092 ms
^C
--- 10.11.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 0.092/0.099/0.114/0.013 ms
root@Sam-EC2:~# ping 10.11.0.2 -I lan2
#Note. ping peer fails
PING 10.11.0.2 (10.11.0.2) from 10.11.0.1 lan2: 56(84) bytes of data.
^C
--- 10.11.0.2 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3061ms
```

```
root@ubuntu:~# ping 10.11.0.2
#note. this is ping lan2 itself on host (ubuntu)
PING 10.11.0.2 (10.11.0.2) 56(84) bytes of data.
64 bytes from 10.11.0.2: icmp_seq=1 ttl=64 time=0.190 ms
64 bytes from 10.11.0.2: icmp_seq=2 ttl=64 time=0.114 ms
64 bytes from 10.11.0.2: icmp_seq=3 ttl=64 time=0.111 ms
64 bytes from 10.11.0.2: icmp_seq=4 ttl=64 time=0.111 ms
^C
--- 10.11.0.2 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3053ms
rtt min/avg/max/mdev = 0.111/0.131/0.190/0.035 ms
```
```
root@ubuntu:~# ping 10.11.0.1
#Note. ping peer fails
PING 10.11.0.1 (10.11.0.1) 56(84) bytes of data.
^C
--- 10.11.0.1 ping statistics ---
17 packets transmitted, 0 received, 100% packet loss, time 16337ms

```
```
root@ubuntu:~# arp -i lan2
#Note. the learnt MAC from 10.11.0.1 EC-2
Address                  HWtype  HWaddress           Flags Mask            Iface
10.11.0.1                ether   00:90:27:ef:c2:d0   C                     lan2
```
```
root@ubuntu:~# ifconfig lan2
lan2      Link encap:Ethernet  HWaddr 00:90:27:ee:f7:c8  
          inet addr:10.11.0.2  Bcast:10.11.0.3  Mask:255.255.255.252
          inet6 addr: fe80::290:27ff:feee:f7c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:118795 (118.7 KB)  TX bytes:133710 (133.7 KB)
```

```
root@ubuntu:~# uname -r
4.15.0-33-generic
root@ubuntu:~#
root@Sam-EC2:~# 
```
```
root@Sam-EC2:~# tcpdump -i lan2 icmp -ne
#Note. only captured "request" packet from "ubuntu" to "EC-2", but no "reply" packet, hence EC-2 doesn't send reply to ubuntu.
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on lan2, link-type EN10MB (Ethernet), capture size 262144 bytes
09:08:08.365456 00:90:27:ee:f7:c8 > 00:90:27:ef:c2:d0, ethertype IPv4 (0x0800), length 98: 10.11.0.2 > 10.11.0.1: ICMP echo request, id 8430, seq 10, length 64
09:08:09.389515 00:90:27:ee:f7:c8 > 00:90:27:ef:c2:d0, ethertype IPv4 (0x0800), length 98: 10.11.0.2 > 10.11.0.1: ICMP echo request, id 8430, seq 11, length 64
09:08:10.413203 00:90:27:ee:f7:c8 > 00:90:27:ef:c2:d0, ethertype IPv4 (0x0800), length 98: 10.11.0.2 > 10.11.0.1: ICMP echo request, id 8430, seq 12, length 64
09:08:11.437574 00:90:27:ee:f7:c8 > 00:90:27:ef:c2:d0, ethertype IPv4 (0x0800), length 98: 10.11.0.2 > 10.11.0.1: ICMP echo request, id 8430, seq 13, length 64
09:08:12.461608 00:90:27:ee:f7:c8 > 00:90:27:ef:c2:d0, ethertype IPv4 (0x0800), length 98: 10.11.0.2 > 10.11.0.1: ICMP echo request, id 8430, seq 14, length 64
^C
5 packets captured
5 packets received by filter
0 packets dropped by kernel
```
```
root@Sam-EC2:~# arp -i lan2
Address                  HWtype  HWaddress           Flags Mask            Iface
bogon                    ether   00:90:27:ee:f7:c8   C                     lan2
root@Sam-EC2:~# ifconfig lan2
lan2      Link encap:Ethernet  HWaddr 00:90:27:ef:c2:d0  
          inet addr:10.11.0.1  Bcast:10.11.0.3  Mask:255.255.255.252
          inet6 addr: fe80::290:27ff:feef:c2d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:321 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26440 (26.4 KB)  TX bytes:6320 (6.3 KB)

```
```
root@Sam-EC2:~# ifconfig blue
blue      Link encap:Ethernet  HWaddr 42:ea:40:25:1b:85  
          UP RUNNING NOARP MASTER  MTU:65536  Metric:1
          RX packets:311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26236 (26.2 KB)  TX bytes:784 (784.0 B)
```

```
root@Sam-EC2:~# uname -r
4.15.0-30-generic
root@Sam-EC2:~# 

```
```
root@Sam-EC2:~# iptables -t nat -vnL
Chain PREROUTING (policy ACCEPT 556 packets, 42242 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 279 packets, 17646 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 2122 packets, 141K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 855 packets, 60734 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 1268 80638 MASQUERADE  all  --  *      wan0    0.0.0.0/0            0.0.0.0/0           
    0     0 MASQUERADE  all  --  *      wan0    0.0.0.0/0            0.0.0.0/0           
root@Sam-EC2:~# 
```

```
root@ubuntu:~# iptables -t nat -vnL
Chain PREROUTING (policy ACCEPT 78909 packets, 9036K bytes)
 pkts bytes target     prot opt in     out     source               destination         
 1097 80781 REDIRECT   udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:53 redir ports 53
95348 4464K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            match-set noproxy dst
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            match-set forbidden dst
    0     0 REDIRECT   udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:53 redir ports 53
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            255.255.255.255      udp dpt:67
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            192.168.20.1         tcp dpt:22
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            192.168.20.1         tcp dpt:80
    0     0 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            match-set US-DNS dst to:192.168.20.1:1061
  906 53888 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            match-set US dst to:192.168.20.1:1061
    0     0 DNAT       udp  --  *      *       0.0.0.0/0            0.0.0.0/0            match-set US-DNS dst to:192.168.20.1:1062
    0     0 DNAT       udp  --  *      *       0.0.0.0/0            0.0.0.0/0            match-set US dst to:192.168.20.1:1062
    0     0 NFQUEUE    icmp --  *      *       0.0.0.0/0            0.0.0.0/0            match-set US-DNS dst NFQUEUE num 0
    0     0 NFQUEUE    icmp --  *      *       0.0.0.0/0            0.0.0.0/0            match-set US dst NFQUEUE num 0

Chain INPUT (policy ACCEPT 939 packets, 61818 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 87517 packets, 5536K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DNAT       tcp  --  *      *       0.0.0.0/0            8.8.8.8              to:192.168.20.1:1061
 1836  130K DNAT       udp  --  *      *       0.0.0.0/0            8.8.8.8              to:192.168.20.1:1062

Chain POSTROUTING (policy ACCEPT 89381 packets, 5669K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 MASQUERADE  all  --  *      wan0    0.0.0.0/0            0.0.0.0/0           
    0     0 MASQUERADE  all  --  *      wan0    0.0.0.0/0            0.0.0.0/0           
root@ubuntu:~#  


```
May I know is any testing setup or methodology incorrect? why the ping over vrf on Linux is unsuccessful?

---

