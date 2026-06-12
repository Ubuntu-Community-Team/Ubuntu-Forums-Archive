---
title: "network issues"
date: 2009-04-28
forum: Server Platforms
---

### Post by root_at_home on 2009-04-28
Hi there.
I upgraded my ubuntu server over the weekend. and after that the network does not come up after a reboot I have to start it manually.
I am running ISP config on the same server.

the other problem is I am getting the following mail.

Warning: service mysqld not running (server: ***.***.***.***)!

Message generated at April 28, 2009, 7:30.

But when I login on the server the mysql is running..

Any help would be great

Root_at_home

---

### Post by Iowan on 2009-04-28
What's in */etc/network/interfaces*?

---

### Post by root_at_home on 2009-04-29
Hi there

this is what is in /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address *.*.*.*
	netmask *.*.*.*
	network *.*.*.*
	broadcast *.*.*.*
	gateway *.*.*.*

Please could you tell me where I can see all the services that starts up with a bootup?

Many thanks

---

