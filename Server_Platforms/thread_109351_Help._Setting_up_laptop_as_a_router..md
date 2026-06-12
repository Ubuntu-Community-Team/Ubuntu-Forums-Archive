---
title: "Help. Setting up laptop as a router."
date: 2005-12-28
forum: Server Platforms
---

### Post by The Warlock on 2005-12-28
Okay, let me explain a bit. I have a laptop that is connected to the Internet through its internal wireless card. 

This laptop also has a normal hardline Ethernet jack and a modem (that Ubuntu seems to detect just fine, although I haven't tested it). 

I would like to set up my laptop so that it could route Internet traffic to a computer or gaming console or whatever that is connected through either the Ethernet jack or, in the case of my old Dreamcast, the modem.

How would I go about doing this? I know it's possible (but a major PITA) in Windows. I'd like to do it in Linux, however.

I have a crossover cable, if that helps. I figure I might need it.

---

### Post by afhp on 2005-12-28
Assuming everything is fine on the wireless side (recognized, connected, getting an address and so on)...

You'll need to enable the wired ethernet interface first. Give it a non-routable address ( 192.168.* ). Let's say 192.168.0.1, the .1 being a usual address (by convention) for a router.

Enable IP forwarding (/etc/network/options).

Make sure that the "default gateway" on this machine is on the wireless connection. (A default gateway is always on the outside network-facing interface).

If you intend to connect several devices/machines, invest in a small switch/hub right away, it'll make life simpler. You could probably find a 5-port for about 20 Euros.

Now, for the rest of the network, you can either :
[LIST]
[*] have the router give out addresses to the other devices. That's probably the easiest way to go. 

Install and set up a DHCP server (eg, dhcp3-server) on the routing machine, it will automatically configure the other machines' IP adresses and routing information.
On the other machines, you'll have to either install or enable the dhcp *client*.

[*] configure the other machines manually. 

Give them each a different IP address in the above range, default gateway 192.168.0.1 (following our example above).
[/LIST]

You'll definitely want to install some firewall software on the router, too. (Well, exactly, all that's needed for firewalling -- "iptables" -- is already included in Linux. What you'll find in the repositories are front-ends to make firewall rules creation and maintenance easier.)

---

