---
title: "Vbox &amp; tun works great, now dns not working in console"
date: 2008-05-29
forum: Virtualisation
---

### Post by orbitron on 2008-05-29
I was able to successfully get vbox working along with setting up the bridging and so far so good.  I have no probs with my guest OSes.

Only problem is now DNS isn't working from the ubuntu console. Here's what I've tried so far:

- was unable to ping yahoo.com or its IP address (66.94.234.13)
- did a **/etc/init.d/networking restart**
- now I can ping 66.94.234.13 but **nslookup yahoo.com** doesn't work
- I can do **telnet 66.94.234.13 80** so I know it isn't a port thing.
- I tried **/etc/init.d/dns-clean force-reload** with no luck.

Any suggestions are appreicated.  Below is the output of **ifconfig**:


```
br0       Link encap:Ethernet  HWaddr 00:09:5b:be:XX:XX 
          inet addr:10.XXX.XXX.XXX  Bcast:10.XXX.XXX.XXX Mask:255.XXX.XXX.XXX
          inet6 addr: fe80::209:5bff:febe:XXXXXX Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6770909 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4421 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1024813043 (977.3 MB)  TX bytes:656605 (641.2 KB)
 
eth0      Link encap:Ethernet  HWaddr 00:09:5b:be:XX:XX
          UP BROADCAST PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xf00 
 
eth1      Link encap:Ethernet  HWaddr 00:0c:f1:92:86:01  
           inet addr:10.XXX.XXX.XXX  Bcast:10.XXX.XXX.XXX Mask:255.XXX.XXX.XXX
          inet6 addr: fe80::20c:f1ff:fe92:XXXXX Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:23104469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1255885 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1251410099 (1.1 GB)  TX bytes:145281361 (138.5 MB)
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:49964 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49964 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17732706 (16.9 MB)  TX bytes:17732706 (16.9 MB)
 
tap0      Link encap:Ethernet  HWaddr 00:ff:de:79:XX:XX  
           inet addr:10.XXX.XXX.XXX  Bcast:10.XXX.XXX.XXX Mask:255.XXX.XXX.XXX
          inet6 addr: fe80::2ff:deff:fe79:XXXXX Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:635 errors:0 dropped:17589033 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:34232 (33.4 KB)  TX bytes:53670 (52.4 KB)
 
tap1      Link encap:Ethernet  HWaddr 00:ff:e6:a7:XX:XX  
          inet6 addr: fe80::2ff:e6ff:fea7:XXXXX Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:17470334 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
tap2      Link encap:Ethernet  HWaddr 00:ff:47:95:XX:XX  
          inet6 addr: fe80::2ff:47ff:fe95:XXXXXX Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1246210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19055718 errors:0 dropped:9 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:149553164 (142.6 MB)  TX bytes:4147185491 (3.8 GB)
```

---

