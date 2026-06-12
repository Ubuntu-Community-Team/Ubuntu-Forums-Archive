---
title: "How do I setup internet and intranet"
date: 2011-12-12
forum: Server Platforms
---

### Post by zylmak on 2011-12-12
Hi I have two servers, both are on Ubuntu

The First server (server1) have an ethernet card ETH0 connected to a router who have access to Internet.

It also have another network card ETH1 connected to another router who DONT have access to the internet

Server2 have only one network card and it is connected to the router who dont have access to the internet


If i try to reach the server1 from the internet everything is fine, if itry to reach the server2 via internet I cant witch is what I want

If i ssh server2 from server1 I can without problem.

The problem from server1 i cant access the internet exactly like if he is trying to connect via eth1 who dont have access to internet

How do I config server1 so he know to use eth0 to access the internet?

here if config

eth0      Link encap:Ethernet  HWaddr 00:06:5b:8c:46:89
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:    255.255.255.0
          inet6 addr: fe80::206:5bff:fe8c:4689/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3010 errors:0 dropped:0 overruns:0 frame:0
          TX packets:756 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:195260 (195.2 KB)  TX bytes:78319 (78.3 KB)

eth1      Link encap:Ethernet  HWaddr 00:0a:5e:04:22:4a
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:5eff:fe04:224a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4393 errors:0 dropped:0 overruns:72 frame:0
          TX packets:825 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1434550 (1.4 MB)  TX bytes:77869 (77.8 KB)
          Interrupt:30 Base address:0x8000
 

and my hosts files
127.0.0.1       localhost.localdomain   localhost
192.168.0.100    server1.mydomain.com      server1
192.168.1.100   server2.mydomain.com      server2

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

### Post by elico on 2011-12-13
use
> route -n
to get the default route setup of your machine.
you will might need to use the 
> ip rule 
command to change the default route priorities on the machine.

---

### Post by zylmak on 2011-12-16
Thanks elico i will try to understand how Route and IP Rule work

I did a lot of test without success the other router who dont have access to the internet alway got the default.

So for now i unpluged the cable and restarted the network and now the server server1 have access to internet.

To access server2 i use a pc with windows connected to both router.

---

