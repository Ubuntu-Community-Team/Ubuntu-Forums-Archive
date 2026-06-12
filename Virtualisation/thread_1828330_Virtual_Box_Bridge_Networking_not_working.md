---
title: "Virtual Box Bridge Networking not working"
date: 2011-08-18
forum: Virtualisation
---

### Post by laxcat on 2011-08-18
I have a win7 host running Virtual box 3.2.10 and an Ubuntu server 2.6 guest.  

I am able to connect from outside (work and host) to the server via ssh and port forwarding on my gateway router to the Ubuntu servers' IP, but the server cant connect out.  The server cant ping the gateway, get updates or anything else.

I opened network adapters from the guest and selected:
Attach to: Bridged Adapter
Name: MAC Bridge Miniport (created by bridging my network adapter with VirtualBox Host-Only Adapter)

**I also tired just connecting it to my network adapter and had the same problem**

---

### Post by lmarmisa on 2011-08-18
Please, post the output of these commands of your Ubuntu server:

```

ifconfig
route -n

```

---

### Post by laxcat on 2011-08-19
I thought it might be something with my network config/iptables maybe I missed something:

```
:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 08:00:27:1b:35:3c
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe1b:353c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7159 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2672322 (2.6 MB)  TX bytes:17082 (17.0 KB)

```

```

:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
```

```
:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
DROP       all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

---

### Post by laxcat on 2011-08-19
```
:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```

---

### Post by laxcat on 2011-08-27
any one got any ideas?

---

### Post by lmarmisa on 2011-09-01
Have you changed the iptables standard rules?.

Do you get the same problem (ping the gateway) changing the network adapter setup to NAT?.

---

