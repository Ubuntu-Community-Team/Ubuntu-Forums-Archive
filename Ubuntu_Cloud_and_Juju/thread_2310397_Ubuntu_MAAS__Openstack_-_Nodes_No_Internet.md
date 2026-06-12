---
title: "Ubuntu MAAS / Openstack - Nodes No Internet"
date: 2016-01-18
forum: Ubuntu Cloud and Juju
---

### Post by Pacific_Coast_Scho on 2016-01-18
[COLOR=#111111][FONT=Ubuntu]I would like to setup an Ubuntu Openstack "super computer" as a class project for my Science and Technology course. However, I am having trouble getting internet to my Nodes. I have tried a myriad of different iptables configurations I found on forums but to no avail. My nodes PXE boot and register with MAAS and I can even power them up through the MAAS GUI. However, the Nodes take about 3 hours to boot up because they can't download from the internet. A brief word on setup:
[/FONT][/COLOR]
```
Public IP - eth0: 192.168.64.5 / 192.168.64.0/24
Private IP - eth1: 10.1.1.1 / 10.1.1.0/24
```

[COLOR=#111111][FONT=Ubuntu]Interestingly I can ping the 10.1.1.1 NIC, or even a Node NIC, from the 192.168.64.x network:
[/FONT][/COLOR]
```
Janzs-iMac:~ jjanz$ ping -c 4 10.1.1.1
PING 10.1.1.1 (10.1.1.1): 56 data bytes
36 bytes from blair-majex.a55blaster (192.168.64.1): Redirect Host(New addr: 192.168.64.5)
Vr HL TOS  Len   ID Flg  off TTL Pro  cks      Src      Dst
4  5  00 0054 150d   0 0000  40  01 59e0 192.168.64.18  10.1.1.1 

64 bytes from 10.1.1.1: icmp_seq=0 ttl=64 time=0.516 ms
36 bytes from blair-majex.a55blaster (192.168.64.1): Redirect Host(New addr: 192.168.64.5)
Vr HL TOS  Len   ID Flg  off TTL Pro  cks      Src      Dst
4  5  00 0054 1771   0 0000  40  01 577c 192.168.64.18  10.1.1.1 

64 bytes from 10.1.1.1: icmp_seq=1 ttl=64 time=0.531 ms
36 bytes from blair-majex.a55blaster (192.168.64.1): Redirect Host(New addr: 192.168.64.5)
Vr HL TOS  Len   ID Flg  off TTL Pro  cks      Src      Dst
4  5  00 0054 6a5a   0 0000  40  01 0493 192.168.64.18  10.1.1.1 

64 bytes from 10.1.1.1: icmp_seq=2 ttl=64 time=0.449 ms
36 bytes from blair-majex.a55blaster (192.168.64.1): Redirect Host(New addr: 192.168.64.5)
Vr HL TOS  Len   ID Flg  off TTL Pro  cks      Src      Dst
4  5  00 0054 dcfb   0 0000  40  01 91f1 192.168.64.18  10.1.1.1 

64 bytes from 10.1.1.1: icmp_seq=3 ttl=64 time=0.465 ms

--- 10.1.1.1 ping statistics ---
4 packets transmitted, 4 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 0.449/0.490/0.531/0.034 ms
```

[COLOR=#111111][FONT=Ubuntu]However when I do the following command from on the MAAS controller:
[/FONT][/COLOR]
```
ping -I eth1 192.168.64.5
``` 

[COLOR=#111111][FONT=Ubuntu]or
[/FONT][/COLOR]
```
ping -I eth1 192.168.64.1
```

[COLOR=#111111][FONT=Ubuntu]I get:[/FONT][/COLOR]

```
python@blare-majex:~$ ping -c 4 -I eth1 192.168.64.5
PING 192.168.64.5 (192.168.64.5) from 10.1.1.1 eth1: 56(84) bytes of data.
From 10.1.1.1 icmp_seq=1 Destination Host Unreachable
From 10.1.1.1 icmp_seq=2 Destination Host Unreachable
From 10.1.1.1 icmp_seq=3 Destination Host Unreachable
From 10.1.1.1 icmp_seq=4 Destination Host Unreachable
```
[COLOR=#111111][FONT=Ubuntu]
I have posted my complete MAAS setup on the following our website with screen shots:[http://sd52.bc.ca/pcs/?p=1633](http://sd52.bc.ca/pcs/?p=1633)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Clearly I'm missing something. Maybe I should start from scratch. I'd like to get this worked out because my students would love to do this project.[/FONT][/COLOR]

---

### Post by Irihapeti on 2016-01-18
*Thread moved to **Ubuntu Cloud and Juju**.*

You'll be more likely to get help here.

---

