---
title: "[SOLVED] Interface used for dynamic DNS service???"
date: 2008-04-14
forum: Server Platforms
---

### Post by x86scorpion on 2008-04-14
Hi there!

I've successfully installed apache webserver using
```
sudo apt-get install apache2
```

and dynDNS client
```
sudo apt-get install ddclient
```

however, I do not know what information to give when it asks
```
"Interface used for dynamic DNS service"
```

What kind of "interface" does it mean? :confused:

----------
I'm on a broadband cable internet with dynamic IP address using
Xubuntu 7.10

---

### Post by Deathrend on 2008-04-14
> **x86scorpion said:**
> What kind of "interface" does it mean? :confused:

type 

```
ifconfig
```

normally it's eth0, but if you have more than one, it could be eth1, eth2, so on, as well as it could be something like "wlan0" or something along those lines for WiFi

I get
```

eth0      Link encap:Ethernet  HWaddr 00:02:a5:ca:8b:45
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:a5ff:feca:8b45/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:137947 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76361 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:69884103 (66.6 MB)  TX bytes:9864556 (9.4 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5932 (5.7 KB)  TX bytes:5932 (5.7 KB)

```

Note: lo is Loopback (Your server) and not what you're looking for.

---

### Post by x86scorpion on 2008-04-14
```
eth0      Link encap:Ethernet  HWaddr 00:14:2A:BF:62:A2  
          inet addr:210.4.117.64  Bcast:210.4.119.255  Mask:255.255.252.0
          inet6 addr: fe80::214:2aff:febf:62a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7697 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9979264 (9.5 MB)  TX bytes:1041463 (1017.0 KB)
          Interrupt:18 Base address:0xee00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5636 (5.5 KB)  TX bytes:5636 (5.5 KB)
```

So basically it asks for my network connection(which is eth0), right?

Well that was quick Deathrend! Thank you very much! :KS

---

### Post by Deathrend on 2008-04-14
I spend most of my day baby sitting servers, so I get time to Troll every so often.  Glad it helped :)

---

