---
title: "Open Directory Server"
date: 2010-07-30
forum: Server Platforms
---

### Post by bsdguyshawn on 2010-07-30
Has anyone setup an ubuntu server as an Open Directory Server for MAX OS X, and other Open Directory clients?

Is it even possible?

---

### Post by brettg on 2010-07-30
As far as I understand it, Open Directory is apple's implementation of openldap server and as such it wont run on ubuntu.

If you want to install openldap on ubuntu then you can [follow this guide]("http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html")

You should then be able authenticate apple clients, but I'm not sure whether extra configuration will be required.

---

