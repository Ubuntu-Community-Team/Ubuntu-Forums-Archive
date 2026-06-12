---
title: "Sharing Internet with 2 cards (with IP fix from ISP)"
date: 2010-07-28
forum: Server Platforms
---

### Post by fsavoir on 2010-07-28
Hi,
I'm trying to share my internet connection on my Ubuntu Server 10.4 (in command line only).
I'm just trying to put the bridge right between my 2 network cards.
I want to first make sure the bridge is working with IP then I will play with NAT.

My /etc/netwok/interfaces file look like that :

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface (for my local network)
auto eth0
iface eth0 inet manual

# The secondary network interface (for my ISP with IP fix)
auto eth1
iface eth1 inet static
        address 81.57.20.200
        netmask 255.255.255.0
        gateway 81.57.20.200
        broadcast 81.57.20.255 

# binding all eths together
auto br0
iface br0 inet static
        address 192.168.1.99
        netmask 255.255.255.0
        gateway 192.168.1.99
        broadcast 192.168.2.255
        network 192.168.0.0
        bridge_ports eth0

Any help? cause I can't ping anything outside my networks.

Thanks for your feedback.

Fred

---

### Post by fsavoir on 2010-07-28
SOLVED :)
Thanks.:KS

---

### Post by mhgsys on 2010-07-28
the OP said cars instead of cards...

Made me interested.

would be nice if you also wrote how you solved it, maybe it comes in handy for other people.

---

