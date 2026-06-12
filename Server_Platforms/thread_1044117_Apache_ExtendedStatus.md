---
title: "Apache ExtendedStatus"
date: 2009-01-19
forum: Server Platforms
---

### Post by MatsB on 2009-01-19
I keep getting this error from my PC which have 192.168.0.10 when I surf to [http://192.168.0.2/server-status:](http://192.168.0.2/server-status:) You don't have permission to access /server-status on this server

I'm running on Ubuntu 8.10 Desktop

This is how i configure it on my server 192.168.0.2 /etc/apache/apache2.conf:


ExtendedStatus On
<Location /server-status>
SetHandler server-status
Order Deny,Allow
Deny from all
Allow from 192.168.0.10
</Location>

I've reloaded apache ofc:


/etc/init.d/apache2 reload

I'm not running any firewall on the Ubuntu PC and both My Windows PC and Ubuntu PC is on the same subnet.

Any ideas?

---

### Post by MatsB on 2009-01-19
I changed the wrong file.

This is the file i changed and now it works:
/etc/apache2/mods-enabled/status.conf

---

