---
title: "Route / Gateway query (2 NICs, PPPoE, simple?)"
date: 2011-07-29
forum: Server Platforms
---

### Post by KennedyM on 2011-07-29
I would greatly appreciate any... pointers... I think the problem may be a trivial one, but I've lost-the-plot!

Using 8.04 LTS, server/router, up-to-date, no GUI, eth0 connected to an ADSL modem (WAN, DHCP, ppp0), and eth1 (192.168.1.250) on the internal LAN (192.168.1.0/24).

DNS running, Firewall (Shorewall), DHCP, etc. All these seem to be OK - but maybe the DNS is broken? I'm experimenting with SIP phones on the LAN side.

Even though there's a GATEWAY entry in the /etc/interfaces file [3], it seems to be ignored, with nothing obvious mentioned in the log-files. The listed routes [1] are created on a fresh boot, with the “default” entry showing no "Gateway" reference. This setup allows the box to access external websites on eth0 (and run “sudo aptitude update”, etc). However, the internal SIP phones on eth1 don't connect to the box.

If I delete the above default route, and manually insert a new default route referring to the box's own IP as Gateway, and on Interface eth1 [2], the command is accepted, the SIP phones connect, but the box itself loses external access. If the new default route refers to Interface ppp0 or eth0, the command is rejected with “SIOCADDRT: No such process”. If the new default route refers to the ISP's GW (and dev=ppp0), the command is accepted, but the phones don't work.

It seems if I could set up the default route to refer to the box itself as Gateway, AND point it at device ppp0, AND then make these settings permanent, the phones and external access would work.

Thank you for any hints...
M.

[1] route -n (WAN access OK):
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
159.134.xxx.xxx 0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
127.0.0.0       0.0.0.0         255.0.0.0       U     0      0        0 lo
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
```
[2] route -n (Phones OK):
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
159.134.xxx.xxx 0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
127.0.0.0       0.0.0.0         255.0.0.0       U     0      0        0 lo
0.0.0.0         192.168.1.250   0.0.0.0         UG    0      0        0 eth1
``` 
[3] /etc/network/interfaces:
```
# The loopback network interface
auto lo
    iface lo inet loopback
    address 127.0.0.1
    netmask 255.0.0.0
    post-up route add -net 127.0.0.0 netmask 255.0.0.0 lo

auto eth0
    iface eth0 inet dhcp
    hwaddress ether 00:14:22:7A:D8:86

auto eth1
    iface eth1 inet static
    address 192.168.1.250
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.250		# ????????
    hwaddress ether 00:10:18:14:8B:F0

auto dsl-provider
    iface dsl-provider inet ppp
    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
    provider dsl-provider
``` 
[4] ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 00:14:22:7a:d8:86  
          inet6 addr: fe80::214:22ff:fe7a:d886/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1603194 (1.5 MB)  TX bytes:84202 (82.2 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:10:18:14:8b:f0  
          inet addr:192.168.1.250  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:18ff:fe14:8bf0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:435 errors:0 dropped:0 overruns:0 frame:0
          TX packets:321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:138641 (135.3 KB)  TX bytes:107785 (105.2 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:289 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100113 (97.7 KB)  TX bytes:100113 (97.7 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:83.71.xxx.xxx  P-t-P:159.134.xxx.xxx  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1564664 (1.4 MB)  TX bytes:42926 (41.9 KB)
```
[5] /etc/resolv.conf:
```
search our.org.local
nameserver 0.0.0.0
```
[6] /etc/sysctl.conf:
```
...includes...
net.ipv4.ip_forward=1
```
[End]

---

