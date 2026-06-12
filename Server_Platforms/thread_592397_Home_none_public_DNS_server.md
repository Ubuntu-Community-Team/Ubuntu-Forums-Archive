---
title: "Home none public DNS server"
date: 2007-10-26
forum: Server Platforms
---

### Post by timgerr on 2007-10-26
Hey all,
I would like to install a home DNS server that is not known outside my lan but will cache inter to external queries.  What do I have to do in order to hide me DNS server from the outside?

Thanks,
timgerr

---

### Post by msund on 2007-10-27
hi mate, the package dnsmasq can create local dns addresses for you, just read through the config file /etc/dnsmasq.conf
its also a dhcp server, so i would read this manual before starting, or else there can be trouble with two dhcp servers on the same net.
[http://linux.die.net/man/8/dnsmasq]("http://linux.die.net/man/8/dnsmasq")

---

