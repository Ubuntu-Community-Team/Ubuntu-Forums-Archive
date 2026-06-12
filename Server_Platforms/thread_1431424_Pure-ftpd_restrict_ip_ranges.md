---
title: "Pure-ftpd restrict ip ranges"
date: 2010-03-16
forum: Server Platforms
---

### Post by lykwydchykyn on 2010-03-16
I have a server running pure-ftpd; I have one virtual user that I want to restrict from logging in via the WAN.  Other users need to be able to log in via WAN

Pure-ftpd supposedly allows me to restrict client IP's, but it's not working.  The account needs to log in from any of several 192.168 networks, and I'd be happy if I could just restrict it to this using deny.hosts-style syntax.

I tried adding:
 192.168

and 
192.168.*.*

But neither allowed me to login from local networks.

I tried using the full CIDR from one of the networks, but it didn't prevent logging in from other networks.

I checked the man page and the online documentation, but neither specifies the syntax for making this particular kind of restriction.

Any pure-ftpd experts know how to accomplish this?

---

### Post by fang0654 on 2010-11-24
I know this is a little old, but I found it while googling for the solution myself.

The proper syntax is 192.168.0.0/16 (or /24 depending on your subnet).

Hope this helps someone else!

---

