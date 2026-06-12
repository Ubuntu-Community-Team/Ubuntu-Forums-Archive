---
title: "Need to ping Guest hostonly adapter from Host"
date: 2011-11-22
forum: Virtualisation
---

### Post by bala150985 on 2011-11-22
Hi

A picture speaks a 1000 words so here is my picture of what I am trying to achieve, Is it possible ?

[IMG]http://www.picvalley.net/v.php?p=u/2790/5857486946308983441321970710bNK6avHdxX6Gpl2ZDLAx.PNG[/IMG]

I am able to ping my Guest's Hostonly adapter IP address when my host Ubuntu does not have a IP to it, however when I try to give it an IP using DHCP I lose the ability to ping my VirtualBox guest's hostonly IP address.

_**When host ubuntu does [COLOR=Red]not[/COLOR] have IP**_
bala@bala-laptop:~$ **ifconfig eth0**
eth0      Link encap:Ethernet  HWaddr 00:12:de:cd:b0:af  
          inet6 addr: fe80::bbbb:aaaa:fe18:a94f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:151981 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:192523623 (192.5 MB)  TX bytes:13485268 (13.4 MB)
          Interrupt:16 
bala@bala-laptop:~$ **route**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.56.0    *               255.255.255.0   U     0      0        0 vboxnet0
bala@bala-laptop:~$ **ping 192.168.56.101**
PING 192.168.56.101 (192.168.56.101) 56(84) bytes of data.
64 bytes from 192.168.56.101: icmp_seq=6 ttl=64 time=11.1 ms
64 bytes from 192.168.56.101: icmp_seq=7 ttl=64 time=0.716 ms
64 bytes from 192.168.56.101: icmp_seq=8 ttl=64 time=0.661 ms
64 bytes from 192.168.56.101: icmp_seq=9 ttl=64 time=0.759 ms
64 bytes from 192.168.56.101: icmp_seq=10 ttl=64 time=0.617 ms

_**When host ubuntu does have IP**_

bala@bala-laptop:~$ **ifconfig eth0**
eth0      Link encap:Ethernet HWaddr 00:12:de:cd:b0:af  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::bbbb:aaaa:fe18:a94f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:151948 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:192517638 (192.5 MB)  TX bytes:13479549 (13.4 MB)
          Interrupt:16 
bala@bala-laptop:~$ **route**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
192.168.56.0    *               255.255.255.0   U     0      0        0 vboxnet0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
bala@bala-laptop:~$** ping 192.168.56.101**
PING 192.168.56.101 (192.168.56.101) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted


Is there any way by which I can get an IP to my host interface and still be able to ping my Guest OS's host only interface?

---

### Post by dcstar on 2011-11-26
> **bala150985 said:**
> 
.........
I am able to ping my Guest's Hostonly adapter IP address when my host Ubuntu does not have a IP to it, however when I try to give it an IP using DHCP I lose the ability to ping my VirtualBox guest's hostonly IP address.
.........

You do know what "Host **only**" means, don't you?

---

