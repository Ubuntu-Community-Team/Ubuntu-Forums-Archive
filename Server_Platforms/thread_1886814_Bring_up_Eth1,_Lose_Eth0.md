---
title: "Bring up Eth1, Lose Eth0"
date: 2011-11-25
forum: Server Platforms
---

### Post by Joseph Duchesne on 2011-11-25
Hi,
I've got two network cards, and am trying to bring a private network online. I am SSHed into the server on eth0, but when I bring eth1 online I lose SSH connection, apache etc. (everything seems dead on eth1). If I bring eth1 offline, eth0 springs to life. 

Here is my /etc/network/interfaces file:
```

auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
  address X.Y.155.55
  netmask 255.255.240.0
  gateway X.Y.144.1
  # dns-* options are implemented by the resolvconf package, if installed
  dns-nameservers X.Y.155.29
  dns-search XY.com

  auto eth0:1
  iface eth0:1 inet static
  address X.Y.155.58
  netmask 255.255.240.0

  auto eth0:2
  iface eth0:2 inet static
  address X.Y.145.11
  netmask 255.255.240.0

  auto eth0:3
  iface eth0:3 inet static
  address X.Y.145.12
  netmask 255.255.240.0

#10.0.0.0/24

auto eth1
iface eth1 inet static
  address 10.0.0.55
  netmask 255.255.255.0
  gateway 10.0.0.1

```

(X.Y are real numbers, I've just redacted them for a bit of server anonymity)

With eth1 down (eth0 working) ifconfig eth0 spits out:
```
eth0      Link encap:Ethernet  HWaddr 00:30:48:83:65:b8
          inet addr:X.Y.155.55  Bcast:X.Y.159.255  Mask:255.255.240.0
          inet6 addr: fe80::230:48ff:fe83:65b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:173351 errors:0 dropped:0 overruns:0 frame:0
          TX packets:177204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:67019067 (67.0 MB)  TX bytes:96192405 (96.1 MB)

```

and with eth1 up (eth0 not working) ifconfig eth0 spits out:
```
eth0      Link encap:Ethernet  HWaddr 00:30:48:83:65:b8
          inet addr:X.Y.155.55  Bcast:X.Y.159.255  Mask:255.255.240.0
          inet6 addr: fe80::230:48ff:fe83:65b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:175372 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179279 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:67842207 (67.8 MB)  TX bytes:97393063 (97.3 MB)

```

I'm really confused.

Edit: 
eth0 does not go down if I bring eth1 up using "ifconfig eth1 up", however this doesn't add the route. When I go to add the route for eth1's gateway (10.0.0.1), eth0 stops responding. The command I use is "sudo route add default gw 10.0.0.1 eth1".

---

### Post by spynappels on 2011-11-25
Howdy!

Just a couple of questions:

Which interface is internet facing?

Also, you can only have one (default) gateway, can you explain why you are trying to set up 2 default gateways?

You can set up a static route if you need to send traffic to a different subnet through a different interface.

---

