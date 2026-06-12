---
title: "Monitor traffic"
date: 2014-09-20
forum: Server Platforms
---

### Post by mmimaa on 2014-09-20
Hi there! I am new to Ubuntu Server and so far it's great. But I have one problem. I'm trying to monitor my traffic and I can't seem to work it out. First, all of my traffic is routed through the loopback interface, therefore RX bytes and TX bytes have the same value, which I think it is the summed value of the upload and download. Furthermore, the reported traffic is much lower than the actual one, like 7.1MB reported and over 750MB transferred manually. I am also using Cacti for those fancy graphs, so I'm posting [this one]("http://i.imgur.com/zYog8db.png") in case it helps. This is the output of 'ifconfig':


```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:88938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7112912 (7.1 MB)  TX bytes:7112912 (7.1 MB)

p3p1      Link encap:Ethernet  HWaddr d0:50:99:28:ab:91
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d250:99ff:fe28:ab91/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19
```

---

### Post by TheFu on 2014-09-20
route?

---

### Post by tgalati4 on 2014-09-20
Loopback is a logical or virtual network connection device to keep services running when a real network is not available.  So you would not monitor the loopback for traffic.  In your case, p3p1 would be the network device, but there is no traffic shown, so something is amiss.

On a laptop:

> tgalati4@Mint14-Extensa ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:ed:ef:1e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:6 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:635325 (635.3 KB)  TX bytes:635325 (635.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:d9:19:fb:ca  
          inet addr:192.168.1.156  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:d9ff:fe19:fbca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31970 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27597 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
         ** RX bytes:20508676 (20.5 MB)  TX bytes:6103841 (6.1 MB)**


*wlan0* is the wireless device that is currently connected.  Thankfully, ubuntuforum traffic is minimal.

---

### Post by vollenweider on 2014-09-21
Don't know if this will help you, but maybe iftop could be of some help in your case.

---

