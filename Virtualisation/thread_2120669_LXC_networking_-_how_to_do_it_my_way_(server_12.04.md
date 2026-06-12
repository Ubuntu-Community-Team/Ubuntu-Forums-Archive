---
title: "LXC networking - how to do it my way? (server 12.04LTS)"
date: 2013-02-27
forum: Virtualisation
---

### Post by RoosterHam on 2013-02-27
So I've played around a little with LXCs on my laptop (lubuntu 12.04) and had great success creating test Asterisk, Nagios, and Pupper-Master containers that I could ssh into and use the services of from my host. This success came practically out of the box, simply adding a static IP address for the containers when I created them.

Now it comes time that I'd like to add these sort of hosts to my home network/lab, and I'd like to use the lightweight lxc to do it. but I am at a loss as to how to configure each container and the host as having individual IP addresses visible from anywhere in my network. Simple adjustments away from the 'out of the box' config keeps breaking things.

I got to the point where I disabled the lxcbr0 and created my own br0, which seemed to work at first. the host's ssh came alive at the IP of br0. The containers' new static IPs didn't respond to anything from the lan, or even from the host.

All the documentation I can seem to find just deals with old releases or creating a natted bridge by hand...

Summary: how to assign one IP to the lxc host machine, and a different unique IP to each container.

---

### Post by RoosterHam on 2013-03-01
so I found the flaws in my config.

1. Had to set the NIC on the physical host to promiscuous mode.[INDENT]This is done with a pre-up statement on br0 bridge interface.
[/INDENT]
2. Set a static IP address and make sure the container's lxc.conf is correct
[INDENT]statements in lxc.conf to link to br0 on the host (lxc.network.link=br0)
set a unique IP in /etc/network/interfaces and I had to set a pre-up route add[/INDENT]

I wasted alot of time because of misunderstanding using the bridge properly. Since I'd only experienced nated bridging I couldn't get my head around how bridge interfaces actually work. looking back at it, I must have had it set up this way for my first experiments, but just didn't realise it.

---

### Post by jeff808 on 2013-04-06
Hi. This is a month old, but if you still around, could you elaborate a little? I'm in the same boat as you and stuck. What do you mean by "set a unique IP in /etc/network/interfaces and I had to set a pre-up route add"? You added the unique IP in the host? As an alias or something? And how/where did you setup the pre-up route?

---

### Post by dcstar on 2013-04-07
[http://lxc.teegra.net/](http://lxc.teegra.net/)

---

