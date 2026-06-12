---
title: "DHCPD/BIND9 question"
date: 2008-09-29
forum: Server Platforms
---

### Post by jerome1232 on 2008-09-29
Currently on my home network I have a server that has dhcp3 and bind9 installed, the dhcp server hands out reserved ip's for each machine I have and bind9 has names assigned to those reserved ips.

I was hoping there's away to get it setup so that:

The server continues to have it's reserved ip and assigned name.
Every other computer that connects gets an ip address assigned through the normal dhcp process, and then updates bind9 with the information and assigns them the same name they have set for their local hostname.

This way let's say I have a computer called 'laptop' it's ip address may change when it connects to the network but the name 'laptop' will all ways be pointing to the correct ip of the machine.

If this is possible; is there a way to catch it when a computer connects that has a duplicate name and not give the new computer a dns entry, just an ip.

---

### Post by lykwydchykyn on 2008-09-29
Check out this howto:

[http://www.cahilig.org/debian-and-ubuntu-ddns-with-bind9-and-dhcp](http://www.cahilig.org/debian-and-ubuntu-ddns-with-bind9-and-dhcp)

---

### Post by jerome1232 on 2008-09-29
Thanks! I'm looking over that how-to and the dhcpd.conf man page right now, and comparing to my current config files to make sense of it all, from what I've read it does everything I want. :)

I was hoping it would work without editing anything on client side.

---

