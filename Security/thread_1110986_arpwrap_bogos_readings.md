---
title: "arpwrap bogos readings"
date: 2009-03-30
forum: Security
---

### Post by [pl]ice on 2009-03-30
Hi there,

Got heaps of arp bogos coming on a server. It got dual RJ45 socket, by disconnecting all users (ie taking the cable out...) the syslog still floods with the arpwatch. If both cables are disconnected, then arpwatch won't show this error.
  So I know there are no other MACs connected to that network, what can be wrong?
some snips:
Mar 30 13:54:20 ro1 arpwatch: bogon 82.160.229.112 0:30:4f:52:21:e3 eth1
Mar 30 13:54:21 ro1 arpwatch: bogon 82.160.229.1 0:1b:21:D:76:fb eth1
Mar 30 13:54:21 ro1 arpwatch: bogon 82.160.229.1 0:1b:21:D:76:fb eth1
Mar 30 13:54:21 ro1 arpwatch: bogon 82.160.229.69 0:1e:68:ab:55:8a eth1
Mar 30 13:54:21 ro1 arpwatch: bogon 82.160.229.1 0:1b:21:D:76:fb eth1
Mar 30 13:54:21 ro1 arpwatch: bogon 82.160.229.1 0:1b:21:D:76:fb eth1


ifconfig:

eth0 Link encap:Ethernet HWaddr 00:1B:21:0D:76:FA
inet addr:82.160.224.170 Bcast:82.160.224.175 Mask:255.255.255.248
inet6 addr: fe80::21b:21ff:fe0d:76fa/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1833529 errors:0 dropped:0 overruns:0 frame:0
TX packets:1506880 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1754317144 (1673.0 Mb) TX bytes:385306303 (367.4 Mb)
Base address:0xb800 Memory:ff7c0000-ff7e0000

eth1 Link encap:Ethernet HWaddr 00:1B:21:0D:76:FB
inet addr:192.168.160.1 Bcast:192.168.160.255 Mask:255.255.255.0
inet6 addr: fe80::21b:21ff:fe0d:76fb/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1519441 errors:0 dropped:0 overruns:0 frame:0
TX packets:1830243 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:386159111 (368.2 Mb) TX bytes:1753255752 (1672.0 Mb)
Base address:0xbc00 Memory:ff7e0000-ff800000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2469 errors:0 dropped:0 overruns:0 frame:0
TX packets:2469 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:223402 (218.1 Kb) TX bytes:223402 (218.1 Kb)

Pls advise, I'm looking into it now, but can't disturb the server too much

---

