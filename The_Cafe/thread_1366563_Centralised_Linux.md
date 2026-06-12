---
title: "Centralised Linux?"
date: 2009-12-28
forum: The Cafe
---

### Post by kevin11951 on 2009-12-28
Is there any way to do the following things?

1. Centralised Login
2. Centralised Home Folders

I am using Ubuntu Servers, and Ubuntu Desktops on a gigabit LAN.

I tried LTSP, but that dosent work, because I want the operating system and applications to be run locally, but just login, and home folders over the LAN.

-Kevin

---

### Post by Xbehave on 2009-12-28
1)LDAP
2)NFS 

I have never used either and there are more advanced alternatives for LDAP, but i think that's where you need to start your search.

---

### Post by koenn on 2009-12-28
yep,
something with ldap and/or kerberos to handle centralised log-on
and nfs to mount user home dirs off a server

---

### Post by Zzl1xndd on 2009-12-28
It is doable, however I have only ever done it with Active Directory and Linux. 

However as other have said for the centralized log in you will want some kind of ldap implementation.

[http://directory.fedoraproject.org/](http://directory.fedoraproject.org/)

and

[http://www.openldap.org/](http://www.openldap.org/) 

might be of some help to you.

---

