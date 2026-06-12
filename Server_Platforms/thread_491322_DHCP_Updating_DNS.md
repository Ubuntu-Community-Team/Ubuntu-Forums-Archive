---
title: "DHCP Updating DNS"
date: 2007-07-03
forum: Server Platforms
---

### Post by jleiss on 2007-07-03
I'm looking for a good tutorial on making the necessary modifications to DNS & DHCP to allow DHCP to update DNS as it is allocating addresses to clients. I am using Dapper Drake 6.06, and have DHCP & DNS up and functioning. The clients will be mostly windows, but could be some linux varieties as well.

---

### Post by koenn on 2007-07-06
If you use dnsmasq as dns+dhcp server, dns will get updated automatically for every dhcp lease. 

If you want the professional approach with bind (named) and dhcpd, it's more tricky. bind can handle dynamic updates from dhcp (or from clients), but you're allowing eg the dhcpd account to write into files owned by the bind account - which is a security problem, that's being handled by an authentication system with keys etc. That makes it more complex. 

here's a Debian howto - most of it is just configuration so it might well work on Ubuntu as well.
[http://www.debian-administration.org/articles/343](http://www.debian-administration.org/articles/343)

---

