---
title: "Managed Desktop Ubuntu"
date: 2008-09-29
forum: Server Platforms
---

### Post by samtay on 2008-09-29
Hey, Everyone

Hope you doing well.

Does anyone have idea on how could I create a Server-Client Network of ubuntu similar to AD?

Cheers
Samuel

---

### Post by lykwydchykyn on 2008-09-29
There isn't a quick and easy answer to this, unfortunately.  The options as I know them are:

 - OpenLDAP: Free, but pretty wide-open.  It's pretty much roll-your-own directory service.
 - Fedora Directory Service: This one's from RedHat, but you can install it on Ubuntu as well.  I believe it's OpenLDAP based, but I have not messed with it.
 - Samba: You can set up an NT-style domain using SAMBA, and configure your ubuntu workstations to authenticate to it.
 - NIS: this was once the standard for Unix authentication, but it's old and notoriously unsecure now.  

There are commercial offerings as well, Canonical offers a tool called "landscape" with commercial support, but I have not tried it to vouch for it.

---

