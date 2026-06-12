---
title: "openldap import data (tree starts with o=...)"
date: 2008-12-26
forum: Server Platforms
---

### Post by elyawm on 2008-12-26
I've installed successfully openldap and imported .ldif in the default tutorial ([https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html)).

Now I want to import another .ldif (exported from my customer). The problem is that the root starts with o=organisation1 and pkg-reconfigure accept only dc=...

How to do to force my root to be like o=... (I'm developing some modification in a customer project, so that, I can't change the structure. I have to import the file as it is).

(.ldif is exported with phpldapadmin which works fine for me using the example on the tutorial and also on the customer server).

(I'm using actually ubuntu 8.10 Desktop).

Thanks.

---

