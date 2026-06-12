---
title: "vmplayer on ubuntu9.04"
date: 2009-07-25
forum: Virtualisation
---

### Post by joe21 on 2009-07-25
Hello!

I use vmware player on Ubuntu 9.04 with 1 windows-xp guest in bridged mode.
"Devices -> Network Adapter" is set up to  Bridged in vmplayer
I have 1 public IP 
Here is my ipconfig output in default mode "Obtain an ip address automatically":

Ethernet adapter Local Area Connection:
 
       Connection-specific DNS Suffix   . :
       IP Address. . . . . . . . . . . . .: 192.168.2.132
       Subnet Mask . . . . . . . . . . . .: 255.255.255.0
       Default Gateway. . . . . . . . . . : 192.168.2.1



And my ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:00:e8:9f:3a:59  
          inet addr:8 .102.37.14   Bcast:8 .102.39.255  Mask:255.255.248.0
          inet6 addr: fe80::200:e8ff:fe9f:3a59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3579198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34889 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:335127883 (335.1 MB)  TX bytes:5144274 (5.1 MB)
          Interrupt:16 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.73.1  Bcast:192.168.73.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.139.1  Bcast:192.168.139.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



My questions are :

why vmnet0 isn't there?

do i have to change to "Use this following IP Address" and implicit Default Gateway and Subnet Mask? 

do i use iptables with POSTROUTING and PREROUTING?
thank's!

---

