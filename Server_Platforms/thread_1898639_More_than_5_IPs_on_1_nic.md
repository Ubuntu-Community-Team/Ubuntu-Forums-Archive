---
title: "More than 5 IPs on 1 nic ?"
date: 2011-12-21
forum: Server Platforms
---

### Post by Nailox on 2011-12-21
Hi. My vps provider is using onAPP. they say it allows them to have up to 5 ips on 1 nic. is it possible to get more than 5 IPs on one nic ? maybe with another system not onAPP? also openvz wont work. I need the interfaces to be listed like eth (not venet like in openvz)

---

### Post by SeijiSensei on 2011-12-23
Linux lets you create an essentially unlimited number of aliases for a single Ethernet interface.  They are defined as eth0:0, eth0:1, etc.  You can assign an IP to one of them with an ifconfig statement like this:

```
sudo ifconfig eth0:0 192.168.1.1 netmask 255.255.255.0 broadcast 192.168.1.255
```

I generally put these in /etc/rc.local (without the "sudo") so they'll be configured during boot.

---

### Post by hawkmage on 2011-12-23
I have used a similar idea but I do it in the /etc/network/interfaces

To test this I put the following in my interfaces file:
```
auto eth0
iface eth0 inet dhcp
  up ip link set dev $IFACE up
  up ip addr add 10.0.2.25/24 broadcast 10.0.2.255 dev eth0 label eth0:1
  up ip addr add 10.0.2.35/24 broadcast 10.0.2.255 dev eth0 label eth0:2
  up ip addr add 10.0.2.45/24 broadcast 10.0.2.255 dev eth0 label eth0:3
  up ip addr add 10.0.2.55/24 broadcast 10.0.2.255 dev eth0 label eth0:4
  up ip addr add 10.0.2.65/24 broadcast 10.0.2.255 dev eth0 label eth0:5
  down ip address flush dev $IFACE
  down ip link set dev $IFACE down
```

I got the following after restarting networking:
```
hawkmage@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:27:67:bb:16  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe67:bb16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4050 (4.0 KB)  TX bytes:11196 (11.1 KB)

eth0:1    Link encap:Ethernet  HWaddr 08:00:27:67:bb:16  
          inet addr:10.0.2.25  Bcast:10.0.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0:2    Link encap:Ethernet  HWaddr 08:00:27:67:bb:16  
          inet addr:10.0.2.35  Bcast:10.0.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0:3    Link encap:Ethernet  HWaddr 08:00:27:67:bb:16  
          inet addr:10.0.2.45  Bcast:10.0.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0:4    Link encap:Ethernet  HWaddr 08:00:27:67:bb:16  
          inet addr:10.0.2.55  Bcast:10.0.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0:5    Link encap:Ethernet  HWaddr 08:00:27:67:bb:16  
          inet addr:10.0.2.65  Bcast:10.0.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
```

---

