---
title: "XEN and two network cards"
date: 2009-08-17
forum: Virtualisation
---

### Post by MattNuzum on 2009-08-17
Hi, I have a server that does not support virtualization instructions. However XEN's paravirtualization seems to be a fine solution. I have one server in my house that I've played with and gotten a basic configuration working. However I'm really focusing on a server that I have installed in a remote datacenter. I installed XEN and a XEN enabled kernel on Friday and rebooted it. Unfortunately it didn't work as well as my test here in my house.

The remote server has two network cards, each connected to a separate network. One network is on the internet via eth0, the other is via eth1 and connects to a private network w/ 192.168.xx.xx addresses.

When I booted the server the only way I could access it was via eth1. eth0 had an assigned IP address but could not ping the Internet nor could the Internet ping it.

I did some searching and some tutorial websites provided what I thought was a good solution (detailed below). unfortunately this solution disabled both network interfaces and I had to do a remote reboot. 

I have to admit that I'm a big newbie when it comes to bridging. I'm very familiar with tcp/ip networking and linux though. I guess that makes me quite foolish for trying to do a remote network install. :-/

**My end goal is to be able to see both networks from Dom0** and create DomUs that can see one or the other network. It might be nice to create a multi-homed domu but that's not a big deal for me at the moment. **Any suggestions on how to pull this off?**

I'm running Ubuntu 9.04 server, XEN 3.3, and here is my network configuration slightly obfuscated (before I messed it up by changing the bridging):

```
$ brctl show
bridge name	bridge id		STP enabled	interfaces
eth0		8000.000000000000	no		
virbr0		8000.000000000000	yes		
```

```
$ ifconfig 
eth0      Link encap:Ethernet  HWaddr ea:5f:d0:d0:c4:ef  
          inet addr:69.60.xxx.96  Bcast:69.60.xxx.255  Mask:255.255.254.0
          inet6 addr: fe80::e85f:d0ff:fed0:c4ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:2694 (2.6 KB)

eth0:1    Link encap:Ethernet  HWaddr ea:5f:d0:d0:c4:ef  
          inet addr:69.60.xxx.106  Bcast:69.60.xxx.255  Mask:255.255.254.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0:2    Link encap:Ethernet  HWaddr ea:5f:d0:d0:c4:ef  
          inet addr:69.60.xxx.107  Bcast:69.60.xxx.255  Mask:255.255.254.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth1      Link encap:Ethernet  HWaddr 00:30:48:55:fa:bb  
          inet addr:192.168.xxx.96  Bcast:192.168.xxx.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe55:fabb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24852 (24.8 KB)  TX bytes:38844 (38.8 KB)
          Interrupt:50 

eth1:1    Link encap:Ethernet  HWaddr 00:30:48:55:fa:bb  
          inet addr:192.168.xxx.106  Bcast:192.168.xxx.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:50 

eth1:2    Link encap:Ethernet  HWaddr 00:30:48:55:fa:bb  
          inet addr:192.168.xxx.107  Bcast:192.168.xxx.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:50 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7286 (7.2 KB)  TX bytes:7286 (7.2 KB)

virbr0    Link encap:Ethernet  HWaddr 5a:f3:c1:a4:11:b0  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::58f3:c1ff:fea4:11b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)
```

What I tried but didn't work:

Replace reference to network-bridge script in xend-config.sxp with a reference to this script instead:

```
#!/bin/sh
dir=$(dirname "$0")
"$dir/network-bridge" "$@" vifnum=0 netdev=eth0 bridge=xenbr0
"$dir/network-bridge" "$@" vifnum=1 netdev=eth1 bridge=xenbr1
```
(from [http://en.opensuse.org/Xen3:_Using_multiple_network_cards](http://en.opensuse.org/Xen3:_Using_multiple_network_cards) )

---

