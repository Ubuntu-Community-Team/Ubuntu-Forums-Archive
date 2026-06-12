---
title: "IPv6 - Network is unreachable"
date: 2013-08-24
forum: Server Platforms
---

### Post by Br_Attila on 2013-08-24
Hello,

I own a Dell Workstation with Ubuntu Server 12.04.

The problem is I can't connect to servers which have IPv6 address.

**ping6 ipv6.google.com**
```
connect: Network is unreachable
```

**ifconfig eth0**

```
eth0      Link encap:Ethernet  HWaddr 64:66:b3:02:9e:37
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6666:b3ff:fe02:9e37/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8804 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6987 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:815539 (815.5 KB)  TX bytes:3813018 (3.8 MB)


```

**cat /etc/network/interfaces**

```

auto lo
iface lo inet loopback
iface lo inet6 loopback

auto eth0
iface eth0 inet dhcp
iface eth0 inet6 auto


```

**route -n**

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0


```

**iptables -L or ip6tables -L**

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


```

**ip -6 route**

```
fe80::/64 dev eth0  proto kernel  metric 256
```

**dmesg | grep IPv6**

```

IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

**ping6 ::1**

```
PING ::1(::1) 56 data bytes
64 bytes from ::1: icmp_seq=1 ttl=64 time=0.041 ms
```

**ping6 fe80::%eth0**

```
PING fe80::%eth0(fe80::) 56 data bytes
From fe80::6670:2ff:fe05:f1b7 icmp_seq=1 Destination unreachable: Address unreachable
```


From Windows 8 the **ping -6 ipv6.google.com** works fine.

My router is : Tp-link TL-R402M

Sry for my bad english.

[SOLVED]

The **iface lo inet6 loopback** solved the problem, but restarting the network itsn't enough. I restarted the Server and solved the problem.

---

### Post by squakie on 2013-08-26
Since you did solve this, please use the "Thread Tools" at the top of the first post and mark the thread as solved.  That will do 2 things:  (1) For people looking for help on a similar problem they know a solution was found and (2) Let others know it is solved so we don't need to look to try to help.

Glad you got your problem solved!

---

