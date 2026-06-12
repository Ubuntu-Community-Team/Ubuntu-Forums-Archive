---
title: "Problems with thin clients (virtual box)"
date: 2008-12-24
forum: Virtualisation
---

### Post by danbar on 2008-12-24
Everything was working fine with my two thin clients till I installed the hplip 2.8.12 (driver for linux for HP printers).

The error command is: failed to add interface to tap0 to the bridge. 

I'm pasting the result of two commands as ROOT.

ifconfig -a
br0       Link encap:Ethernet  HWaddr 00:19:66:3c:71:0a 
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::219:66ff:fe3c:710a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3251 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2646 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2319067 (2.3 MB)  TX bytes:419462 (419.4 KB)

eth0      Link encap:Ethernet  HWaddr 00:19:66:3c:71:0a 
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::219:66ff:fe3c:710a/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:3279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2369176 (2.3 MB)  TX bytes:431531 (431.5 KB)
          Interrupt:22 Base address:0xb800

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6214 (6.2 KB)  TX bytes:6214 (6.2 KB)

pan0      Link encap:Ethernet  HWaddr 16:74:2f:f2:b2:80 
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap0      Link encap:Ethernet  HWaddr ce:33:f8:8a:40:6f 
          inet6 addr: fe80::cc33:f8ff:fe8a:406f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:251 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap1      Link encap:Ethernet  HWaddr c6:6a:6d:e1:f7:6a 
          inet6 addr: fe80::c46a:6dff:fee1:f76a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:248 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


brctl show
bridge name    bridge id        STP enabled    interfaces
br0        8000.0019663c710a    no        eth0
                            tap0
                            tap1
pan0        8000.000000000000    no

---

