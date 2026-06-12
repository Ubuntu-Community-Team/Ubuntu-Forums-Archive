---
title: "Ubuntu one doesn't detect my internet connection"
date: 2011-06-20
forum: Ubuntu One (CLOSED)
---

### Post by R00$ter on 2011-06-20
**Hi, i am using an USB ADSL modem i have set it up correctly and now i get this when i issue the ifconfig command**

[I]eth0      Link encap:Ethernet  HWaddr 00:1d:72:6e:20:1b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:261 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34901 (34.9 KB)  TX bytes:34901 (34.9 KB)

nas0      Link encap:Ethernet  HWaddr 00:d0:41:6d:c8:0d  
          inet6 addr: fe80::2d0:41ff:fe6d:c80d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10735 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9804150 (9.8 MB)  TX bytes:2052218 (2.0 MB)

nas0:avahi Link encap:Ethernet  HWaddr 00:d0:41:6d:c8:0d  
          inet addr:169.254.6.251  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:41.203.-.-  P-t-P:41.203.-.- Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:10643 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:9714695 (9.7 MB)  TX bytes:1680128 (1.6 MB)[/I]

**Now my question is: how to get UbuntuOne to detect my internet connection?**

---

### Post by mike1312 on 2011-07-19
I have the same problem on natty. I dont use network manager because of [this]("http://ubuntuforums.org/showthread.php?p=10989757#post10989757") problem.
Ubuntu One application says that there is no connection while im surfing the internet.

---

