---
title: "bridge wlan interface, for use with openvpn"
date: 2010-12-20
forum: Server Platforms
---

### Post by artheus on 2010-12-20
Hey!

I've been searching around a bit, and can't really find out what I am doing wrong.
What I want to do is to set up a simple bridge for my openvpn server to work with.

I've used this tutorial.
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

But the problem is that my server is using Wlan/WPA2-PSK, to connect to the LAN and WAN. So therefore I've configured my /etc/network/interfaces like so:

```

auto br0
auto wlan0

iface wlan0 inet manual
    wpa-conf /etc/wpa_supplicant.conf

iface br0 inet static
    address 192.168.1.2
    netmask 255.255.255.0
    gateway 192.168.1.1
    network 192.168.1.0
    broadcast 192.168.1.255
    bridge_ports wlan0

```

I have tested the wlan0 configuration without the br0 and that worked fine. And I've tested some different approaches for configuration, but no luck at all.

Does anyone know how to do this?

Cheers,
Arthes

---

### Post by artheus on 2010-12-21
I'm sorry about this... but..... bump..

---

