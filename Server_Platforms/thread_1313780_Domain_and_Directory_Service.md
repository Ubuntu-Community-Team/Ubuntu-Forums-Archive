---
title: "Domain and Directory Service"
date: 2009-11-04
forum: Server Platforms
---

### Post by afhkhan on 2009-11-04
Hi All,

I want to setup a domain on Ubuntu and create a centralized repository of users and resources like Active Directory. Pls advise if it is possible. If yes, how?

Many Thanks

---

### Post by BQAggie2006 on 2009-11-04
This can be accomplished a number of different ways, mixing NIS, OpenLDAP, Kerberos, NFS, Samba, etc.

It depends on what kind of environment you are going to be running it in. If it's just a Linux environment, you can probably get away with using OpenLDAP+NFS.

If you are going to be mixing Windows and Linux, an LDAP+Samba solution is probably what you will want to look into.

The Ubuntu Server Guide has a few good sections covering the second option.

---

