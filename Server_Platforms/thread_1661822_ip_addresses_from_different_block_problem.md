---
title: "ip addresses from different block problem"
date: 2011-01-07
forum: Server Platforms
---

### Post by ilsilent on 2011-01-07
I have an Ubuntu 10.04 Server machine with a single nic, eth1.
I have to manage multiple public ip addresses assigned to my server, so my /etc/network/interfaces looks like this:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
  address 93.144.21.15
  netmask 255.255.255.0
  network 93.144.21.0
  broadcast 93.144.21.255
  gateway 93.144.21.1
  up ip addr add 93.144.21.116 brd 93.144.21.255 dev eth0 label eth0:1
  up ip addr add 93.144.21.117 brd 93.144.21.255 dev eth0 label eth0:2
  up ip addr add 103.164.163.40 brd 103.164.163.255 dev eth0 label eth0:3

```

THE PROBLEM IS THE FOLLOWING: even if I can ping the last managed address (103.164.163.40), every connection I attempt to that ip is refused by the server, no matter which port I use. The other ip addresses seems ok.

What can cause the connection to be refused only for that particular ip?

ps: Shorewall is installed and running as server firewall.

---

### Post by ilsilent on 2011-01-07
Seems that the problem was not mine, but ISP's. I changed my last ip address and reported the malfunction.

---

