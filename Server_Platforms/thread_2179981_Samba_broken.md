---
title: "Samba broken"
date: 2013-10-10
forum: Server Platforms
---

### Post by trevor_obba on 2013-10-10
I configured freeradius version 2.2.0 running on Ubuntu 12.04 to authenticate against active directory and it is working fine until I decide to clone (vmware) the machine.

Once the machine is clone I changed the IP address, hostname in (/etc/hosts and /etc/hostname) and also changed the name in /etc/samba/smb.conf

Finally I tried to join the clone machine using “net join –U administrator” unfortunately this break the original freeradius machine by no longer authenticating to active directory and the clone machine will not join the Domain also.

I think the clone machine is still referring the original machine which breaks the original machine unfortunately I do not know how to fix it.

How do I fix the original machine?
What else do I change on the clone machine so that I can successfully join it to domain with breaking the original machine?

---

