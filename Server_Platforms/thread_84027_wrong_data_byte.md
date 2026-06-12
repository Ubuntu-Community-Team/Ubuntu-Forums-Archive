---
title: "wrong data byte"
date: 2005-10-30
forum: Server Platforms
---

### Post by mat3 on 2005-10-30
Hi.

I've recently set up ubuntu 5.10 as a server with dhcp. It's been working since yesterday. Yesterday I replaced processor with p III 533MHz and now computers in my network haven't got net.

When I tried to ping one of computers I got something like this:

```
mate@magdam:~$ ping 192.168.0.5
PING 192.168.0.5 (192.168.0.5): 56 data bytes
64 bytes from 192.168.0.5: icmp_seq=0 ttl=128 time=0.7 ms
64 bytes from 192.168.0.5: icmp_seq=2 ttl=128 time=1.0 ms
64 bytes from 192.168.0.5: icmp_seq=3 ttl=128 time=0.6 ms
64 bytes from 192.168.0.5: icmp_seq=4 ttl=128 time=0.4 ms
wrong data byte #46 should be 0x2e but was 0xee
        14 15 16 17 18 19 1a 1b 1c 1d 1e 1f 20 21 22 23 24 25 26 27 28 29 2a 2b 2c 2d ee 2f 7c 2f 32 33
        34 35 36 37 0 0 0 0 9c dc 5 8 ff ff ff ff
64 bytes from 192.168.0.5: icmp_seq=5 ttl=128 time=0.4 ms
64 bytes from 192.168.0.5: icmp_seq=6 ttl=128 time=0.4 ms
64 bytes from 192.168.0.5: icmp_seq=7 ttl=128 time=0.4 ms
64 bytes from 192.168.0.5: icmp_seq=8 ttl=128 time=0.4 ms
64 bytes from 192.168.0.5: icmp_seq=10 ttl=128 time=0.4 ms
wrong data byte #34 should be 0x22 but was 0x2a
        14 15 16 17 18 19 1a 1b 1c 1d 1e 1f 20 21 2a 23 24 25 26 27 28 29 2a 2b 2c 2d 2e 2f 30 31 32 33
        34 35 36 37 0 0 0 0 9c dc 5 8 ff ff ff ff
64 bytes from 192.168.0.5: icmp_seq=11 ttl=128 time=0.4 ms

--- 192.168.0.5 ping statistics ---
13 packets transmitted, 10 packets received, 23% packet loss
round-trip min/avg/max = 0.4/0.5/1.0 ms

```

When i tried ping server I got very high packet loss.

I've just replaced NIC and it's the same problem.

additional info:


```
mate@magdam:~$ ifconfig -a eth0      Link encap:Ethernet  HWaddr 00:02:44:35:53:18
          inet addr:192.168.49.124  Bcast:192.168.49.255  Mask:255.255.248.0
          inet6 addr: fe80::202:44ff:fe35:5318/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:166235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2255 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13041874 (12.4 MiB)  TX bytes:322672 (315.1 KiB)
          Interrupt:11 Base address:0xe800

eth1      Link encap:Ethernet  HWaddr 00:02:44:82:5D:0E
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:44ff:fe82:5d0e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:653 errors:0 dropped:0 overruns:0 frame:0
          TX packets:315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:66322 (64.7 KiB)  TX bytes:28026 (27.3 KiB)
          Interrupt:5 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16759 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16759 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1305366 (1.2 MiB)  TX bytes:1305366 (1.2 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

```
mate@magdam:~$ route -n Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.48.0    0.0.0.0         255.255.248.0   U     0      0        0 eth0
0.0.0.0         192.168.48.1    0.0.0.0         UG    0      0        0 eth0

```

help me, please :(

---

### Post by mat3 on 2005-10-30
ok i've solved this problem. 

it's strange but i had to overclock processor :o :o :o :o and now it works fine :D

---

