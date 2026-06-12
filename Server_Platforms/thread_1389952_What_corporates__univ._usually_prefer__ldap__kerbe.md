---
title: "What corporates / univ. usually prefer : ldap / kerberos / smb / ... for the network?"
date: 2010-01-25
forum: Server Platforms
---

### Post by frenchn00b on 2010-01-25
Hello,

Managing quantities of users can with linux be well managed since many years. Usually what is the choice of universities or big organization with linux based servers? 

How do they basically usually manage the passwords and users files, for linux, mac, and windows machines on the overall network?

Kerberos, ldap, or smb? or all together...

---

### Post by Lars Noodén on 2010-01-25
Whether they know it or not, they are probably using for authentication Kerberos and OpenLDAP to manage group membership.  The level of skill and knowledge at most sites, though, it now such that you will likely get blank stares except from a very small few. 

Both are very easy to set up and Kerberos in particular is useful in a distributed computing environment because of [easy replication](http://tldp.org/HOWTO/Kerberos-Infrastructure-HOWTO/server-replication.html).  The two implementations, Heimdal and MIT, are interoperable.  

Samba uses both and will help a lot if it takes a while to phase out any Windows dekstops.  Mac OS X, Solaris, BSD, and any Linux all work easily with plain Kerberos + OpenLDAP.

---

