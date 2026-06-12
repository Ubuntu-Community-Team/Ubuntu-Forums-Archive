---
title: "Apache not accessible despite router forwarding ports"
date: 2012-04-11
forum: Server Platforms
---

### Post by ralfzurich on 2012-04-11
Hi to everybody,

my Ubuntu 11.10 box is running behind a router. The router is the gateway to my ISP. The Ubuntu box has static ip on eth0 and dhcp on wlan0. Here is the ifconfig output:
```

eth0      Link encap:Ethernet  HWaddr 00:16:d4:64:b0:70
          inet addr:192.168.1.150  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe64:b070/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4937 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1318628 (1.3 MB)  TX bytes:5174168 (5.1 MB)
          Interrupt:21 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:622175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:622175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:214717030 (214.7 MB)  TX bytes:214717030 (214.7 MB)

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:0b:b4:98
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7eff:fe0b:b498/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1235606 (1.2 MB)  TX bytes:3765466 (3.7 MB)

```On the Ubuntu box I'm running Apache and would like to access it from outside my LAN. I registered at dyndns.org, configured the router to log in there, and enabled port forwarding for ports 80 (http) and 22 (ssh) to the eth0 static ip . 

I'm able to access the web server from inside the LAN by using the dyndns.org URL.
I'm able to access the box by ssh from inside the LAN also by using the dyndns.org URL.
Both does not work from outside my LAN.

However, what works from outside my LAN by using the dyndns.org URL is to access an Apache running on a Windows PC at port 8081 (provided I forward that port through the router). That's why I think it is an Ubuntu box issue and not a router issue.

I checked iptables. All have policy ACCEPT in all chains and no rules defined.

Any idea around what's wrong? Thanks in advance for your valuable advice :)

Kind regards
Ralf

---

### Post by darkod on 2012-04-11
And if you try from outside your LAN but using the public IP of the router, not the dyndns address. Does it open apache/website?

---

### Post by ralfzurich on 2012-04-12
No, it didn't. I tried this previously. However, now it works. What I did are two things: I disabled the WLAN and in the BIOS boot sequence I moved the boot from ethernet beyond the boot from hard disk, which seemed to be the way they booted the computer before I bought the box. It is not a new one.

Kind regards
Ralf

---

