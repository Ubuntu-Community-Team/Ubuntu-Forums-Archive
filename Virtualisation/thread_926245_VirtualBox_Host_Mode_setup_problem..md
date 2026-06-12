---
title: "VirtualBox Host Mode setup problem."
date: 2008-09-21
forum: Virtualisation
---

### Post by pwaugh on 2008-09-21
Well, after reading several tutorials, reference books, and the VBox manual I'm not quite there.

In the end, I need to run a process (a debugger) on a virtual XP (the company does not support Linux), and connect to it from Eclipse running on Ubuntu.

After installing XP on vbox, I setup the first NIC to do NAT, and this works fine, and a 2nd to do Host.

Here is my /etc/network/interfaces:

# Define interfaces which are auto
auto lo eth0 br0

# Loopback Interface
iface	lo		inet	loopback

# Ethernet 0 Interface
iface	eth0	inet	static
address 192.168.1.2
netmask 255.255.255.0

# Bridge
iface	br0		inet	dhcp
	bridge-ports eth0

I have setup my ubuntu box to use a static IP so I can easily port-fwd to it later to do some other things.

My first question is:  How can I test to see if I can see my XP "host" so I know it's working?

I have been able to get to my shared directory that I created, but now how can I connect to a running app, and see my XP host on the LAN?

Patrick

---

