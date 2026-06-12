---
title: "packet error probability"
date: 2009-04-24
forum: Server Platforms
---

### Post by cdenley on 2009-04-24
I'm trying to compute the general probability that an uploaded file (FTP or HTTP) would be corrupt. As I understand it, the only way this could happen is if a TCP packet contains 2 errors which cancel each other out. The only server I have which seems to have corrected errors is an ubuntu firewall which I have configured as a bridge between the router and the rest of the network.
```

cdenley@firewall:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:0c:41:e9:da:5d  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:41ff:fee9:da5d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2068684608 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1521304267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:637366796 (607.8 MB)  TX bytes:3603603604 (3.3 GB)

eth0      Link encap:Ethernet  HWaddr 00:0c:41:e9:da:5d  
          inet6 addr: fe80::20c:41ff:fee9:da5d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          **RX packets:2434923502 errors:53** dropped:0 overruns:0 frame:83
          TX packets:2442631202 errors:780 dropped:0 overruns:0 carrier:1384
          collisions:0 txqueuelen:1000 
          RX bytes:4269441341 (3.9 GB)  TX bytes:1480331968 (1.3 GB)
          Interrupt:11 Base address:0xd800 

eth1      Link encap:Ethernet  HWaddr 00:0c:41:e9:da:62  
          inet6 addr: fe80::20c:41ff:fee9:da62/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          **RX packets:927326917 errors:134** dropped:0 overruns:0 frame:196
          TX packets:910868078 errors:36450 dropped:0 overruns:0 carrier:66510
          collisions:0 txqueuelen:1000 
          RX bytes:3481531880 (3.2 GB)  TX bytes:1067773018 (1018.3 MB)
          Interrupt:10 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:499097 (487.3 KB)  TX bytes:499097 (487.3 KB)

```
I used the number of errors in received packets (bold) since uploaded files would be received by us? Would these numbers be an accurate representation of the probability of errors in packets sent by users uploading files? Why do transmitted packets seem to have many more errors? I'm assuming the other servers don't have any errors because they are caught by the bridge and the packet is resent by the sender before being forwarded by the bridge. Is this correct? Is there something that might increase the number of corrected errors such as a malicious attack?

I'm also calculating based on the assumption that the probability of an uncorrected error (U) in a packet is half the probability of two corrected errors (C) in a packet (C^2 / 2 = U).

Another assumption is 1,480 bytes of file data per packet.

Anybody have any ideas for my calculation, corrections on my assumptions, or know where/how I can obtain statistics which may help?

Also, anyone know a calculator application which handles very precise decimal values? Gcalctool seems to round down to zero if the result is small enough, I'm assuming because of a limitation with the float/decimal variable type it uses.

---

