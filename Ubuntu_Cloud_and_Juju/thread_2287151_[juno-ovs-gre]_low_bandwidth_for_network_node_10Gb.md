---
title: "[juno-ovs-gre] low bandwidth for network node 10Gb nic (but around 3Gb/s only)"
date: 2015-07-17
forum: Ubuntu Cloud and Juju
---

### Post by vuquangkha on 2015-07-17
Hi all,
I am using ubuntu 14.04.2, juno version, and neutron + openvswitch gre.

This is my diagram:

[IMG]http://s23.postimg.org/4ob8pnaff/diagram.jpg[/IMG]


Network node: external network, data network in a nic.
i tested bandwidth:
from physical network node to multiple physical compute node enough 10Gb/s
[IMG]http://s7.postimg.org/karma6yon/network_to_compute.jpg[/IMG]

But network node to multiple instance around 3.5Gb/s
[IMG]http://s8.postimg.org/3mm3t549t/network_to_instance.jpg[/IMG]

And external server to multiple instance around 3Gb/s
[IMG]http://s13.postimg.org/rwtk210gj/external_to_instance.jpg[/IMG]


(from network node to a instance enough 1Gb/s)
All not enough 10Gb/s
I searched multiple days, try MTU 9000,...
but can not, i don't know why.
HELP ME.
THANKS ALL VERY MUCH !

---

