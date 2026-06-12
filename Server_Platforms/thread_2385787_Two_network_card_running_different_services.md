---
title: "Two network card running different services"
date: 2018-02-25
forum: Server Platforms
---

### Post by kandai93 on 2018-02-25
Hi there,

Im using ubuntu server 14.04. The device have two NIC running different network (eno1 and eno2). My concern is about eno1, i want to enable eno1 to send and receive multicast form network 239.x.x.x. Do i need to add for 239.x.x.x network ?  i have add routing configuration below, is my routing running well ?


[LIST]
[*]eno1 - connected to internal network with static IP (Gateway 192.168.1.1) (vlan 1000)
[*]eno2 - connected to Internet. (Gateway 10.10.1.1) (vlan 1001)
[/LIST]
[FONT=inherit]##Network Configuration##
```

#internet connection

auto eno2
iface eno2 inet static
address 10.10.1.5
netmask 255.255.255.0
gateway 10.10.1.1
dns-nameservers 8.8.8.8

#internal network

auto eno1
iface eno1 inet static
address 192.168.1.5
netmask 255.255.255.0

#routing configuration

up route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.1.1 dev eno1
up route delete default gw 192.168.1.1 dev eno1
up route add default gw 10.10.1.1 dev eno2


```

[/FONT]

---

### Post by wildmanne39 on 2018-02-25
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

