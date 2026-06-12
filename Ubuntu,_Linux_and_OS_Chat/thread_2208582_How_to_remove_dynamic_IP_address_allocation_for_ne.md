---
title: "How to remove dynamic IP address allocation for network interface in ubuntu 12.04??"
date: 2014-03-01
forum: Ubuntu, Linux and OS Chat
---

### Post by venkatesh484 on 2014-03-01
Hello,

[FONT=arial][SIZE=2]I have [/SIZE][/FONT][FONT=arial]plugged[/FONT][FONT=arial][SIZE=2] in 9 network interfaces to my server and planning to use one for physical host and other's for virtualbox VM's. [/SIZE][/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I have installed ubuntu 12.04 on my server and configured eth0 static ip but ips were allocated for all the interfaces from eth0 to eth8 dynamically.

Could you please let me know how to remove dynamic IP address allocation for my network interface eth1 to eth8?

Thanks,
Venkatesh. [/FONT]

---

### Post by ian-weisser on 2014-03-01
Do you mean that you have nine real ethernet cables plugged into nine physical NICs?
Or do you mean that you have one real ethernet cable and nine of host adapter interfaces?

Check the VM networking settings and the assigned IP addresses:
Are the VMs getting IP addresses from the VM host (that's one of it's services), or from your LAN's dhcp server?

---

### Post by venkatesh484 on 2014-03-01
Hello Ian,

I have nine real ethernet cables plugged into nine physical NICs.I have configured static ips for my physical host and VM's. (Eth0 for physical and ETH1 to eth8 for virtualbox).


Issue: I have configured only eth0 static in /etc/network/interfaces on my physical host but somehow ips got allocated for remaining interfaces eth1 to eth8 from dhcp on physical hostlevel which I do not want because I need to use them for my virtualbox.


Could you please let me know how to disable dynimic ip allocation on my physical host?


```
root@gopr01:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
address 10.82.xx.xx
netmask 255.255.255.0
gateway 10.82.xx.1
```
```
root@gopr01:~# ifconfig
eth0      Link encap:Ethernet  HWaddr bc:30:5b:da:f7:43
          inet addr:10.82.65.61  Bcast:10.82.65.255  Mask:255.255.255.0
          inet6 addr: fe80::be30:5bff:feda:f743/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19419 errors:0 dropped:26 overruns:0 frame:0
          TX packets:13587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1975470 (1.9 MB)  TX bytes:15895861 (15.8 MB)
          Interrupt:17


eth1      Link encap:Ethernet  HWaddr 00:10:18:9d:fb:8a
          inet addr:172.16.1.210  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:18ff:fe9d:fb8a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1010 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1521271 (1.5 MB)  TX bytes:180017 (180.0 KB)


eth2      Link encap:Ethernet  HWaddr 00:10:18:9f:5a:a0
          inet6 addr: fe80::210:18ff:fe9f:5aa0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5684521 (5.6 MB)  TX bytes:3873640 (3.8 MB)


eth3      Link encap:Ethernet  HWaddr 00:10:18:9f:5a:a2
          inet addr:172.16.1.85  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:18ff:fe9f:5aa2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15613 errors:0 dropped:0 overruns:0 frame:0
          TX packets:610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1412695 (1.4 MB)  TX bytes:126701 (126.7 KB)


eth4      Link encap:Ethernet  HWaddr 00:10:18:94:93:74
          inet addr:172.16.1.186  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:18ff:fe94:9374/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15617 errors:0 dropped:0 overruns:0 frame:0
          TX packets:600 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1414887 (1.4 MB)  TX bytes:124576 (124.5 KB)


eth5      Link encap:Ethernet  HWaddr 00:10:18:94:93:76
          inet addr:172.16.1.197  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:18ff:fe94:9376/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31093 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16213 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2584607 (2.5 MB)  TX bytes:1144087 (1.1 MB)


eth6      Link encap:Ethernet  HWaddr 00:10:18:9f:5d:1c
          inet addr:172.16.1.234  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:18ff:fe9f:5d1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15566 errors:0 dropped:0 overruns:0 frame:0
          TX packets:571 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1402468 (1.4 MB)  TX bytes:120640 (120.6 KB)


eth7      Link encap:Ethernet  HWaddr 00:10:18:9f:5d:1e
          inet addr:172.16.1.18  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:18ff:fe9f:5d1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:561 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1432910 (1.4 MB)  TX bytes:118140 (118.1 KB)


eth8      Link encap:Ethernet  HWaddr 00:10:18:9d:fb:88
          inet addr:172.16.1.235  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:18ff:fe9d:fb88/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15632 errors:0 dropped:0 overruns:0 frame:0
          TX packets:650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1427626 (1.4 MB)  TX bytes:127640 (127.6 KB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:52802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:127701962 (127.7 MB)  TX bytes:127701962 (127.7 MB)


root@gopr01:~#
```

---

### Post by ian-weisser on 2014-03-01
Are those perhaps the IPs assigned by Virtualbox?
If not, you have a rather unusual router setting.

---

### Post by venkatesh484 on 2014-03-02
I got a solution from below link

[http://lastoctet.com/2009/04/12/bring-up-interface-in-debian-ubuntu-with/](http://lastoctet.com/2009/04/12/bring-up-interface-in-debian-ubuntu-with/)

---

