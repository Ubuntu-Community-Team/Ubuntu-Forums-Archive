---
title: "need to add different gateway / ip-number"
date: 2012-07-30
forum: Server Platforms
---

### Post by antennanl on 2012-07-30
Dear All,

We have serveral ip-numbers active on a server and got from the hosting centre an extra ip-number, however this time with a different gateway.

My current /etc/network/interfaces below
How can I have the following added:
IP: 178.63.109.86
Gateway: 178.63.109.65
Maske: 255.255.255.224

Thanks,

Tsjêbbe

# Loopback device:
auto lo
iface lo inet loopback

# device: eth0
auto  eth0
iface eth0 inet static
        address 78.46.102.67
        broadcast 78.46.102.95
        netmask 255.255.255.224
        gateway 78.46.102.65
        addresses 78.47.245.145/32 78.47.245.146/32 78.47.245.147/32 78.47.245.148/32 78.47.245.149/32 78.47.245.150/32 178.63.109.92/32
        up route add -net 78.46.102.64 netmask 255.255.255.224 gw 78.46.102.65 eth0
        post-up iptables-restore < /etc/iptables.up.rules

---

### Post by BkkBonanza on 2012-07-30
You can create a virtual interface and config it with correct details just like eth0.

eg. add a section like this,

auto eth0:1
iface eth0:1 inet static
address 178.63.109.86
netmask 255.255.255.224
gateway 178.63.109.65

then you can use **sudo ifup eth0:1** to bring it up for testing.

---

