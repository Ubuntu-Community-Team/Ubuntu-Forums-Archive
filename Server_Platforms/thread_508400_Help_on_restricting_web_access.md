---
title: "Help on restricting web access"
date: 2007-07-24
forum: Server Platforms
---

### Post by catech on 2007-07-24
Hi,

I have a client who wants the following.

A solution which would allow general users to acces only 1 website. Managers need to have access to any website.

The client also wants a network share, which I could samba.

I was thinking of a Samba PDC, and using something like squid for internet restrictions. Anyone know a better way?

James

---

### Post by sjoerger on 2007-07-24
Depending on the clients environment you could do the web filtering with router acl's or iptables/firewall rules.

---

### Post by catech on 2007-07-27
All the clients are 2k/XP clients. How would I set the firewall to determine who is allowed to access and who isn't?

---

### Post by bmathis on 2007-07-27
i use this setup at work, i use squid and dansguardian with iptables and squid acls to determine which clients get what access (dansguardian blocks all porn and illegal sites, great for the kids too). If you go the router way, you can make rules based on MAC addresses.

---

