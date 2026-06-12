---
title: "IPv6 unavaliable after idle"
date: 2013-03-24
forum: Server Platforms
---

### Post by iWader on 2013-03-24
I have several Ubuntu 12.04.2 64bit server VMs running under XenServer 6.1. 

Whenever they are left for ~30 mins with no traffic over ipv6, the network becomes unavailable, requiring the restart of the networking service to bring it back up. IPv4 is still active.

```
:~# ping6 google.com
connect: Network is unreachable
```

They are able to ping other VMs running on the same Host OS, but nothing above the host, even though the host and other VMs have IPv6 access.

Any help is appreciated. Wader

---

### Post by sanderj on 2013-03-25
What kind of IPv6 are you using?

What is the output of:

```
mtr -nrc2 ipv6.google.com
dmesg | grep -i ipv6
ip -6 addr show
```

---

### Post by iWader on 2013-03-25
Its native IPv6 provided by OVH

mtr -nrc2 ipv6.google.com

```
:~# mtr -nrc2 ipv6.google.com
HOST: lithium.iwader.co.uk        Loss%   Snt   Last   Avg  Best  Wrst StDev
```

dmesg | grep -i ipv6

```
:~# dmesg | grep -i ipv6
[    2.693689] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.693694] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
```

ip -6 addr show

```
:~# ip -6 addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qlen 1000
    inet6 2607:5300:60:2f30::2/64 scope global
       valid_lft forever preferred_lft forever
    inet6 fe80::ff:fe5b:19b/64 scope link
       valid_lft forever preferred_lft forever

```

---

### Post by sanderj on 2013-03-25
What kind of network is between the host and the guest OS? NAT? Bridged? ... ?

Maybe the first next hop (host OS or router) forgets the route to guest OS. Or maybe the guest OS does not answer ICMP6-who-has requests?

---

### Post by iWader on 2013-03-25
> **sanderj said:**
> What kind of network is between the host and the guest OS? NAT? Bridged? ... ?

Maybe the first next hop (host OS or router) forgets the route to guest OS. Or maybe the guest OS does not answer ICMP6-who-has requests?

Its running under routed networking. My host (OVH) doesn't allow bridged adapters.

The kernel provided by OVH for the host os (XenServer 6.1) its pre-configured for both ipv4 and ipv6 routed networking, so i dont think the issues lies there.

---

### Post by sanderj on 2013-03-25
Routed? So the Host is taking care of *routing*?

Oh, wait: is the XenServer provided by OVH? If so, ask them what is going on.

---

### Post by sanderj on 2013-03-25
PS:

What does

```
rdisc6 eth0

```
tell you?

---

### Post by iWader on 2013-03-25
> **sanderj said:**
> Routed? So the Host is taking care of *routing*?

Oh, wait: is the XenServer provided by OVH? If so, ask them what is going on.

Yes, all traffic from the VMs must be routed through the host os rather than directly connecting to their network. I already have a post on their forums, not very active though, doubt i would get help via. ticket

> **sanderj said:**
> PS:

What does

```
rdisc6 eth0

```
tell you?

```
:~# rdisc6 eth0
Soliciting ff02::2 (ff02::2) on eth0...


Hop limit                 :           64 (      0x40)
Stateful address conf.    :           No
Stateful other conf.      :           No
Router preference         :       medium
Router lifetime           :         1800 (0x00000708) seconds
Reachable time            :  unspecified (0x00000000)
Retransmit time           :  unspecified (0x00000000)
 Source link-layer address: 6C:9C:ED:BA:EC:40
 MTU                      :         1500 bytes (valid)
 Prefix                   : 2607:5300:60:2f00::/56
  Valid time              :      2592000 (0x00278d00) seconds
  Pref. time              :       604800 (0x00093a80) seconds
 from fe80::6e9c:edff:feba:ec40


Hop limit                 :           64 (      0x40)
Stateful address conf.    :           No
Stateful other conf.      :           No
Router preference         :       medium
Router lifetime           :         1800 (0x00000708) seconds
Reachable time            :  unspecified (0x00000000)
Retransmit time           :  unspecified (0x00000000)
 Source link-layer address: 6C:9C:ED:BA:EB:40
 MTU                      :         1500 bytes (valid)
 Prefix                   : 2607:5300:60:2f00::/56
  Valid time              :      2592000 (0x00278d00) seconds
  Pref. time              :       604800 (0x00093a80) seconds
 from fe80::6e9c:edff:feba:eb40
```

---

### Post by lemming465 on 2013-03-26
So, are there supposed to be two upstream routers?

---

