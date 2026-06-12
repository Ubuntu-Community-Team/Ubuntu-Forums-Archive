---
title: "Bind ip adress"
date: 2011-09-30
forum: Server Platforms
---

### Post by mujahied on 2011-09-30
Hi all ,

i have a issue i have modified /etc/network/interfaces

and "/etc/network/interfaces.head" and "/etc/network/interfaces.tail"

and the information in all of the files is the same but still the 

auto lo
iface lo inet loopback

# Auto generated venet0 interface
auto venet0
iface venet0 inet manual
        up ifconfig venet0 up
        up ifconfig venet0 0
        up route add default dev venet0
        down route del default dev venet0
        down ifconfig venet0 down



auto venet0
iface venet0 inet static
        address xxxxxxxxxxxxx
        netmask xxxxxxxxxxxx



But still when i run ifconfig this is not displayed where does venet0:0 come from 

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:xxxxxxxxxxx P-t-P:xxxxxxxxxx Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1

---

### Post by spynappels on 2011-09-30
Have a look at this:

[http://wiki.openvz.org/Virtual_network_device](http://wiki.openvz.org/Virtual_network_device)

It suggests how to configure network interfaces on OpenVZ deployments.

Google is your friend!

---

### Post by mujahied on 2011-09-30
i need to bind my ip adres on the venet0 

it shows on venet0:0

---

