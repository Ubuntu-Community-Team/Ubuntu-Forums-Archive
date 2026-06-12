---
title: "server vpn"
date: 2012-11-11
forum: Server Platforms
---

### Post by Craigst on 2012-11-11
looking for someone that has set up vpn on a vps before as i having issues connecting , i think its to do with etc/network/interface file with i have to edit via /interface.template

as i dont have eth0 interface only virtual connection


auto lo
iface lo inet loopback
        address 127.0.0.1
        netmask 255.0.0.0
        broadcast 127.255.255.255
        up ip route replace 127.0.0.0/8 dev lo

root@s16366520:~# ip route
191.255.255.1 dev venet0  scope link
127.0.0.0/8 dev lo  scope link
default via 191.255.255.1 dev venet0

root@s16366520:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
191.255.255.1   *               255.255.255.255 UH    0      0        0 venet0
127.0.0.0       *               255.0.0.0       U     0      0        0 lo
default         191.255.255.1   0.0.0.0         UG    0      0        0 venet0


any input will be helpfull

i will be connecting iphone, ipad, pc and laptop

regards craig

---

