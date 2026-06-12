---
title: "Virtual Box NAT Networks - No Internet Access"
date: 2015-08-11
forum: Virtualisation
---

### Post by ehsan8 on 2015-08-11
I have created a aNAT Network in VirtulBox 5 In Ubuntu 14.04 LTS with followingsettings
 
Natework Name :NatNetwrok1
Network CIDR:10.0.2.0/24
Support DHCP:enabled
Support IPv6:disabled
without any portforwarding

Additionally I havetwo VMs (Both Xubuntu clones), I have set the Network settings toenable  two NICs on each of the VM with following settings in allfour adapters:

Attached To     : “NATNetwork” 
Name        :“NatNetwrok1”

When I run both VMsI can see following settings on running ifconfig command

**ifconfig results onXubuntu1**

**eth0**   Linkencap:Ethernet  HWaddr 08:00:27:00:8c:03  
          inetaddr:10.0.2.9  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6addr: fe80::a00:27ff:fe00:8c03/64 Scope:Link
          UPBROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RXpackets:43 errors:0 dropped:0 overruns:0 frame:0
          TXpackets:47 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
          RXbytes:12133 (12.1 KB)  TX bytes:8517 (8.5 KB)

**eth1**  Linkencap:Ethernet  HWaddr 08:00:27:9e:20:e8  
          inetaddr:10.0.2.8  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6addr: fe80::a00:27ff:fe9e:20e8/64 Scope:Link
          UPBROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RXpackets:43 errors:0 dropped:0 overruns:0 frame:0
          TXpackets:48 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
          RXbytes:10294 (10.2 KB)  TX bytes:8798 (8.7 KB)

**ifconfig results onXubutracentu2**

**eth0**   Linkencap:Ethernet  HWaddr 08:00:27:00:8c:03  
          inetaddr:10.0.2.9  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6addr: fe80::a00:27ff:fe00:8c03/64 Scope:Link
          UPBROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RXpackets:43 errors:0 dropped:0 overruns:0 frame:0
          TXpackets:47 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
          RXbytes:12133 (12.1 KB)  TX bytes:8517 (8.5 KB)

**eth1**   Linkencap:Ethernet  HWaddr 08:00:27:9e:20:e8  
          inetaddr:10.0.2.8  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6addr: fe80::a00:27ff:fe9e:20e8/64 Scope:Link
          UPBROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RXpackets:43 errors:0 dropped:0 overruns:0 frame:0
          TXpackets:48 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
          RXbytes:10294 (10.2 KB)  TX bytes:8798 (8.7 KB)


Ping between these 4IPs works fine 
But I can not accessInternet on either of these VMs
While if o change“NAT Network” to “NAT” I can access the network but it seemsthe become part of different virtual network and I can not ping themfrom each other
Can anybody help mein identifying and fixing problem

---

