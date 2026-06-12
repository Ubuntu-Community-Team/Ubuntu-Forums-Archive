---
title: "Ubuntu 15.10 virtual machine no networking functionality."
date: 2016-02-12
forum: Virtualisation
---

### Post by mark267 on 2016-02-12
In OpenStack I launch a Ubuntu 15.10 image, choosing settings including network that was created in Contrail Cloud Platform SDN. This instance will not obtain a DHCP IP address on this network and does not get network connectivity. Other images I have launched have no problem. If I assign a static IP address to this instance it gets network connectivity. However, what network it thinks it is on I don't know. it cannot ping other instance on that network and vice versa and it cannot ping the gateway on that network either. When this instance is set to DHCP, Contrail networking & OpenStack thinks it was assigned an IP address. Contrail networking and OpenStack have even allocated a port on the virtual switch for the instance, and Contrail networking and OpenStack even report this instance's MAC address. Yet this instance does not get an IP address, is not on the network, and no tap interface is created for it.

ifconfig
[B][http://tinyurl.com/gqbe8uc](http://tinyurl.com/gqbe8uc)

[/B]cat /etc/network/interfaces
[B][B][http://tinyurl.com/h8z6xfl](http://tinyurl.com/h8z6xfl)
[/B]
[/B]lshw -C network
**[B][http://tinyurl.com/hufep2e](http://tinyurl.com/hufep2e)**

[/B]cat /etc/NetworkManager/NetworkManager.conf
[B][URL="http://tinyurl.com/gqbe8uc"][B][http://tinyurl.com/ztssp2j](http://tinyurl.com/ztssp2j)
[/B][/URL][/B][B][URL="http://tinyurl.com/gqbe8uc"]
[/URL]
[/B][URL="http://tinyurl.com/gqbe8uc"][U][COLOR=#000000]2nd Ubuntu VM instance launched on OpenStack - Juniper Contrail SDN environment and exhibits the same networking issues as other Ubuntu VM. One VM is version 15.10 and one is version 14.04. Have deployed multiple Cirros and CentOS VM instances with no networking problems at all. Problem seems to be specifically related to Ubuntu. Anyone with any ideas? 
[/COLOR][/U][/URL]

---

### Post by MAFoElffen on 2016-02-13
From one of your working Centos containers, please post
```

cat /etc/sysconfig/network-scripts/ifcfg-eth0
cat /etc/sysconfig/network
ifconfig -a

```
From you Ubuntu 15.10 container, please post:
```

cat /etc/network/interfaces

```
The 3 pic's you linked to... are all the same link, which repeatedly shows your ifconig output with no IP assigned.

---

