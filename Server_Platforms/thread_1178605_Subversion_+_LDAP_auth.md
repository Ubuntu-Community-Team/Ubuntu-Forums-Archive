---
title: "Subversion + LDAP auth"
date: 2009-06-04
forum: Server Platforms
---

### Post by Alekz_ on 2009-06-04
Hi everyone!

I'd like to know if somebody have already setup Subversion authenticating with OpenLDAP.

I know it's possible (google it), but I'm still unable to get it running!

Important information:
Ubuntu 8.04
OpenLDAP 2.4.16
Subversion 1.6.2

I'm not using the Ubuntu Repository Packages! I'm using the tarball source and compiling it (need to be this way because I won't use Ubuntu in production).

Thanks! :)

---

### Post by HDave on 2009-09-21
As far as I know, everybody doing LDAP authentication for subversion is doing it inside of Apache via WebDAV.  I can't find anybody doing it natively with the svn protocol, although it is possible if you know how to navigate SASL.

There are how-tos on subversion/ldap/apache all over the place.

---

