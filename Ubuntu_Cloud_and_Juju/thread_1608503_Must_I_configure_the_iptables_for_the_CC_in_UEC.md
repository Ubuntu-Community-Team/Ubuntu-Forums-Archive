---
title: "Must I configure the iptables for the CC in UEC?"
date: 2010-10-29
forum: Ubuntu Cloud and Juju
---

### Post by philipprince on 2010-10-29
Dear All,

I am constructing a UEC private cloud within my local network 192.168.123.0 (Gateway and DNS server are both 192.168.123.1). I cannot communicate from the NC on 192.168.20.2 out to the DNS server (or anywhere else outside of 192.168.20.X).

I am not clever so I have been scrupulously following steps in the Eucalyptus Beginner's Guide - UEC Edition while using the installation wizard for Ubuntu 10.10 Server (AMD64).

The configuration is intended to look like:

CLC (192.168.123.151) 
  <-> switch1 <-> 
CC (eth0:192.168.123.152,eth1:192.168.20.1)
  <-> switch2 <-> 
NC (eth1:192.168.20.2)

I can ping the CLC from the CC, the NC from the CC, the CC from the NC but I cannot ping anywhere else from the NC.

The CLC interface is:
auto eth0
iface eth0 inet static
    address 192.168.123.151
    netmask 255.255.255.0
    network 192.168.123.0
    broadcast 192.168.123.255
    gateway 192.168.123.1
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.123.1
    dns-search oxil.co.uk

There is a switch between CLC and CC.

The CC interface is:
auto eth0
iface eth0 inet static
    address 192.168.123.152
    netmask 255.255.255.0
    network 192.168.123.0
    broadcast 192.168.123.255
    gateway 192.168.123.1
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.123.1
    dns-search oxil.co.uk

auto eth1
iface eth1 inet static
address 192.168.20.1
netmask 255.255.255.0
network 192.168.20.0
broadcast 192.168.20.255

There is a different switch between CC and NC.

The NC interface is:
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
    address 192.168.20.2
    netmask 255.255.255.0
    network 192.168.20.0
    broadcast 192.168.20.255
    gateway 192.168.20.1
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.123.1
    dns-search oxil.co.uk
    bridge_ports eth0
    bride_fd 9
    bridge_hello 2
    bridge_maxage 12
    bridge_stp off

In resolv.conf:
search oxil.co.uk
nameserver 192.168.123.1

A colleague suggests that the iptables have not been configured to pass traffic through the CC to the outer world. 

On the CC "cat /proc/sys/net/ipv4/ip_forward" yields 1. It is at this point that I have stopped as I am reluctant to change iptable settings without any understanding.

Where should I go next?

Many thanks,
Philip

---

### Post by philipprince on 2010-10-29
I have taken this from [http://www.howtoforge.com/nat_iptables](http://www.howtoforge.com/nat_iptables).

iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE
iptables --append FORWARD --in-interface eth1 -j ACCEPT

The communication out is now possible so something simple like "apt-get update" now works.

Is this the right thing to do? If so, where should I put it? I tried rc.local but it was ignored.

---

