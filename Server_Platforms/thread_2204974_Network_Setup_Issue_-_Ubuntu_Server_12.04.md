---
title: "Network Setup Issue - Ubuntu Server 12.04"
date: 2014-02-11
forum: Server Platforms
---

### Post by Joshua_Thomas on 2014-02-11
Hello. I am setting up an Ubuntu server running 12.04 and having issues with the network. I can ping the localhost, but not the gateway or any other system on the network. Here is my ifconfig and route -n information:

eth0  Link encap: Ethernet HWaddr 00:14:2a:bd:6a:ba
        inet addr:XX.XXX.XXX.166 Bcast:XX.XXX.XXX.167 Mask:255.255.255.248
        UP BROADCAST MULTICAST MTU:1500 Metric:1

Destination          Gateway               Genmask              Flags      Metric      Rcf       Usc      Iface
0.0.0.0               XX.XXX.XXX.161     0.0.0.0                UG         100          0          0         eth0
XX.XXX.XX.160    0.0.0.0                  255.255.255.248   U           0             0          0         eth0

Here are the contents of /etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
     address XX.XXX.XXX.166
     netmask 255.255.255.248
     network XX.XXX.XXX.160
     broadcast XX.XXX.XXX.167
     gateway XX.XXX.XXX.161

     dns name-servers 209.18.47.61 XX.XXX.XXX.161


Any thoughts on what the problem might be?

---

### Post by Joshua_Thomas on 2014-02-11
Nevermind; issue resolved. In all my checking of the system, I neglected to notice that the ethernet cable was slightly unplugged. *rolls eyes*

---

