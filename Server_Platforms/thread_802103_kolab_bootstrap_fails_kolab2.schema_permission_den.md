---
title: "kolab bootstrap fails: kolab2.schema permission denied"
date: 2008-05-21
forum: Server Platforms
---

### Post by scotty64 on 2008-05-21
When I am running kolab_bootstrap -b to configure kolab everything works fine until it comes to the temporary start of slapd. This fails and a check when trying to start slapd in debugging mode reveals this:

line 24 (include /usr/share/kolabd/schema/kolab2.schema)
could not open config file "/usr/share/kolabd/schema/kolab2.schema": Permission denied (13)

This is odd, because all the schemas in /etc/ldap/schemas have exactly the same permissions as kolab2.schema.

Any ideas ?

---

### Post by enigma_0Z on 2008-07-29
Same issue here. Any results yet?

---

### Post by Stewart9643 on 2010-08-11
I had several attempts at installing Kolab on 10.4 with all sorts of issues. I've re-instlalled Ubuntu that many times I've almost worn out the HD. I tried it from source, from the packages etc on installs from a bsic ubuntu server config to a server setup with full LAMP. 
Bootstrapping being a major issue. On the latest headbanging episode on a full LAMP install on 10.4 using the package I stopped all servers, run bootstrap and accidently went right thru the setup without touching any settings including the password. Damned if it didn't work.  Now to work out why it can't find my LDAP server.

---

