---
title: "NETWORK SERVER SETUP info"
date: 2011-11-04
forum: Security
---

### Post by Flaggmann on 2011-11-04
I need a bit of explanation on setting up a home dns server.  I have followed the step by step instructions for "The Perfect Server" for various distros, and although it is clear and simple setting up, the big picture so one understands it all is somewhat vague.

I would like the bind daemon to run and relay to outside world, yet maintain the local LAN w/s's so they don't crap out and reset the nic addresses to default s in the 169series like windoze does.

I have tried ISPConfig under "The Perfect Server" option and like it, but again it lacks a lot of detail for understanding.

Second can someone give me a simple explanation on netmasking. As I understand it if I set a standard Class C home net to a netmask 255.255.0.0 I should be able to run 254 w's on each of 254 subnets. Would that be correct?

Sorry if this isn't exact forum to post to but could find one that fit my questions exactly. Thanx

---

### Post by CharlesA on 2011-11-04
I'd rather use dnsmasq instead of a full blow BIND server for a local dns server.

Much easier to configure.

Subnetting can get a bit complicated but you can only run 254 hosts on a class C network.

192.168.x.1 to 192.168.x.254

192.168.x.0 and 192.168.x.255 are not used for hosts.

Having a subnet of 255.255.0.0, would make a class B network.

---

