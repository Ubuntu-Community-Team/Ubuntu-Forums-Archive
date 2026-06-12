---
title: "Ubuntu Server losing network connectivity"
date: 2011-03-22
forum: Server Platforms
---

### Post by oybed on 2011-03-22
Hi
I installed a 8.04 LTS server. The server (the hardware) was previously running Fedora without issues. However, after installing Ubuntu Server I keep losing the network connectivity pretty often. All the configuration seems to be good and all I have to do when losing the connectivity is to use the console to ping some other host, etc. from the server and things are back to working condition again. I've tried multiple Ethernet cards and same issue. FYI: This installation doesn't have NetworkManager installed (at least it doesn't appear to).
 
I'm running many different Linux distros and Ubuntu is the only one where I've seen this. Anybody seen this before and know what can be causing it? It seems to be some sort of a software timeout/power save, etc.

---

### Post by arrrghhh on 2011-03-22
NetworkManager would never run on a server (no GUI).

As for why, can you elaborate on your network setup?  Do you have static IP addresses?

---

### Post by oybed on 2011-03-22
Yes, it's setup with staticially assigned IP address:
 
```
 
>> cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.209.199
    netmask 255.255.254.0
    network 192.168.208.0
    broadcast 192.168.209.255
    gateway 192.168.209.254
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.1.1
    dns-search mylocaldomain.com
 
>> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:5e:cd:44:5a
          inet addr:192.168.209.199  Bcast:192.168.209.255  Mask:255.255.254.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:45316 (44.2 KB)  TX bytes:47708 (46.5 KB)
          Interrupt:16
 
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20088 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20088 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9765551 (9.3 MB)  TX bytes:9765551 (9.3 MB)
 
>> route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.208.0   0.0.0.0         255.255.254.0   U     0      0        0 eth0
0.0.0.0         192.168.209.254 0.0.0.0         UG    100    0        0 eth0

```

---

