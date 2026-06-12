---
title: "drbl server and dhcp"
date: 2012-07-06
forum: Server Platforms
---

### Post by Hanspeter Heeb on 2012-07-06
I installed a drbl server on an old machine.

It connects to the web correctly.

ifconfig shows:
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:48:d2:74  
          inet addr:192.168.100.100  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe48:d274/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1567 errors:0 dropped:0 overruns:0 frame:0
          TX packets:563 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:222104 (222.1 KB)  TX bytes:99199 (99.1 KB)

eth1      Link encap:Ethernet  HWaddr 00:30:f1:04:f2:d5  
          inet addr:192.168.101.254  Bcast:192.168.101.255  Mask:255.255.255.0
          inet6 addr: fe80::230:f1ff:fe04:f2d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:237 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82872 (82.8 KB)  TX bytes:16896 (16.8 KB)
          Interrupt:18 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8344 (8.3 KB)  TX bytes:8344 (8.3 KB)

I connected a laptop directy to eth1. Unfortunately it does not receive an ip nor can it connect to the network. How can I find the mistake? Any suggestions?

---

### Post by SeijiSensei on 2012-07-06
You cannot connect one machine to another with a standard Ethernet cable.  You need to use either an Ethernet hub or switch, or something called a "crossover" cable.  The crossover cable connects the transmit pins in the Ethernet jack on one machine to the receive pins on the other, and vice versa.

---

