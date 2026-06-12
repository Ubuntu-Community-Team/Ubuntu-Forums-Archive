---
title: "Network is unreachable in Ubuntu 14.04 on Virtualbox using bridged adaptor staic ip"
date: 2015-11-05
forum: Virtualisation
---

### Post by Edmond_Ching on 2015-11-05
I got Network is unreachable in Ubuntu 14.04 on Virtualbox using bridged adaptor as a VM server.

In /etc/network/interfaces:

auto lo
iface lo inet loopback


source /etc/network/interfaces.d/*.cfg


auto eth0
iface eth0 inet static
      address 192.168.1.198
      netmask 255.255.255.0

to ifconfig command:


eth0      Link encap:Ethernet  HWaddr 08:00:27:f2:f2:d9  
          inet addr:192.168.1.198  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fef2:f2d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52985 errors:0 dropped:168 overruns:0 frame:0
          TX packets:11637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6703018 (6.7 MB)  TX bytes:7075821 (7.0 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:15858 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5983872 (5.9 MB)  TX bytes:5983872 (5.9 MB)

If I ran ping to other internal device such as 192.168.1.* then it is working. If I ran ping 8.8.8.8, it showed Network is unreachable. Is there any setting I am missing?
Thanks a lot

---

### Post by SeijiSensei on 2015-11-05
Do you have a default route that points to your upstream router?  Try running
```
sudo ip route add default via 192.168.1.1
```
assuming that is the address of your router.

If that solves the problem, you can fix it permanently by adding a 
```
gateway 192.168.1.1
```
directive after the "netmask" line in the stanza for eth0.

---

### Post by Edmond_Ching on 2015-11-05
It works. Thanks so much

---

