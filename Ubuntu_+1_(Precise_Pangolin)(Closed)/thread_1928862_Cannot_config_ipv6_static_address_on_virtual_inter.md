---
title: "Cannot config ipv6 static address on virtual interface."
date: 2012-02-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by cty1976 on 2012-02-20
I cannot assign any ipv6 static address for my ubuntu 12.04 by using the following configuration:


# The loopback interface
auto lo
  iface lo inet loopback
    address 127.0.0.1
    netmask 255.0.0.0

# The prime wired interface
auto eth0
# iface eth0 inet dhcp
  iface eth0 inet static
    address 172.19.33.136
    netmask 255.255.255.0
    gateway 172.19.33.1
  iface eth0 inet6 static
    address 2000:1::1
    netmask 64
    gateway 2000:1::1

# virtual interfaces
auto eth0.199
  iface eth0.199 inet static
    address 172.19.100.1
    netmask 255.255.255.0
    gateway 172.19.100.1
  iface eth0.199 inet6 static
    address 2000:199::1
    netmask 64
    gateway 2000:199::1
    pre-up    echo 0 > /proc/sys/net/ipv6/conf/eth0.199/autoconf
    post-down echo 1 > /proc/sys/net/ipv6/conf/eth0.199/autoconf
    up   /sbin/ifconfig eth0.199 inet6 add 2000:199::1/64
    down /sbin/ifconfig eth0.199 inet6 del 2000:199::1/64

The ipv6 address for eth0 is all right, bu cannot work on eth0.199. Anyone can give some clue for this issue? Thank you.:confused:

---

### Post by cty1976 on 2012-02-21
:-(:-(:-(

---

### Post by edder on 2012-02-22
you dont realy need to use a virtual interface, just add as many ipv6 addresses to eth0 as you need.

---

### Post by dino99 on 2012-02-22
During past hours we got some new updated packages related to ipv6, should work better now, especially ipv6 is called now before ipv4.

---

