---
title: "Can't ping From ubuntu host to ZeroShell Guest using VirtualBox"
date: 2013-02-13
forum: Virtualisation
---

### Post by jesh on 2013-02-13
Hello! sorry for my bad english I hope you can help me.
Here's my problem:
I have virtualbox installed in ubuntu 12.04 runing zeroShell and I have 3 ethernet interfaces eth0, eth1, eth2. I use 2 interfaces for internet balancing (eth0 and eth1), and eth2 helps to bring out the zeroshell conection to the network. I configured the eth's as bridged mode. I can ping the eth0 and eth1 from the host to the guest and backwards, but i can't ping eth2. If i connect a Pc trhough the eth2 it gets me the connection as it should.

Heres my network interfaces:
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.70
netmask 255.255.255.0
gateway 192.168.1.254
dns-nameservers 192.168.1.254

auto eth1
iface eth1 inet static
address 192.168.0.70
netmask 255.255.255.0

auto eth2
iface eth2 inet static
address 192.168.2.2
netmask 255.255.255.0

---

