---
title: "ufw on vrf interface not allowing connections"
date: 2020-05-12
forum: Server Platforms
---

### Post by sbuxhofer on 2020-05-12
I configured vrf on ubuntu 18.04 and 20.04, enabled SSH service. I can connect to ssh via eth1 as long UFW is disabled, once UFW is enabled I cannot connect to any vrf interface any longer. I tried adding explicity rules for the IP address on the interface and accept on eth1 incoming to no avail. UFW logging does not log any discarded packets. With tcpdump, I can see the packets coming in, however nothing is being sent out.

Is UFW not supposed to work on VRF interfaces? Or is there a special configuration I am missing?

Network config:
```
::::::::::::::
eth0.network
::::::::::::::
[Match]
Name = eth0


[Network]
Description = Interface eth0 
DHCP = v4
IPv6AcceptRA = true
::::::::::::::
eth1.network
::::::::::::::
[Match]
Name = eth1


[Network]
Description = Interface eth1 VRF
DHCP = yes
VRF=vrf20
::::::::::::::
vrf20.netdev
::::::::::::::
[NetDev]
Name=vrf20
Kind=vrf


[VRF]
TableId=1020
::::::::::::::
vrf20.network
::::::::::::::
[Match]
Name = vrf20


[Network]
DHCP = no
BindCarrier=lo
```

sysctl.conf
```
net.ipv4.tcp_l3mdev_accept = 1
net.ipv4.udp_l3mdev_accept = 1
```

Simple ufw config:

```
ufw status numberedStatus: active


     To                         Action      From
     --                         ------      ----
[ 1] 22/tcp                     ALLOW IN    Anywhere                  
[ 2] 22/tcp (v6)                ALLOW IN    Anywhere (v6) 
```

---

