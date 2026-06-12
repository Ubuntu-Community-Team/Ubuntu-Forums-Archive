---
title: "Problem with virtual network interface/alias and connecting to guests"
date: 2009-06-24
forum: Virtualisation
---

### Post by Mogga on 2009-06-24
So I've almost got things working the way I want them too for my home testing setup... (See the attached jpeg)

The problems I'm having are as follows:
1) I'm not convinced that the bridge approach is correct - seems like it should be aliases with ip forwarding but not an expert on these things
2) I can see the host server 10.1.0.1 from my 192.168.1.0 network but can't see the guest machines 10.1.0.2 etc.... Weird thing is that if I'm on the host machine I CAN see them

Here's my /etc/network/interfaces file:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
	bridge_ports eth0
	bridge_hello 2
	bridge_maxage 12
	bridge_stp on
	bridge_maxwait 5
	address 192.168.1.50
	netmask 255.255.255.0
	broadcast 192.168.1.255
	network 192.168.1.0
	gateway 192.168.1.254

auto eth0:1
iface eth0:1 inet static
	address 0.0.0.0
	netmask 0.0.0.0

auto br0:1
iface br0:1 inet static
	bridge_ports eth0:1
	bridge_hello 2
	bridge_maxage 12
	bridge_stp on
	bridge_maxwait 5
	address 10.1.0.1
	netmask 255.255.0.0
	broadcast 10.1.255.255
	network 10.1.0.0

```

I've seen other approaches that use TUN/TAP but I haven't a clue how to make this work for my scenario.

Any help is appreciated. It's been a fun learning experience thus far...

---

