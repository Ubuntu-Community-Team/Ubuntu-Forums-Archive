---
title: "Question on domain name for LDAP"
date: 2008-02-10
forum: Server Platforms
---

### Post by cpthk on 2008-02-10
In openLDAP, we have to set up domain name like: dn = cn=admin,dc=example,dc=local

What if my company does have a domain name? We just have regular DSL connection. Will that still work? Can't openLDAP go through ip address?

---

### Post by dpiddy on 2008-02-24
The top of your LDAP tree doesn't have to be a real domain name. I'd recommend using something ending in dc=local like in your example. Such as:

dc=yourcompany,dc=local

---

### Post by astrotech226 on 2008-02-24
The top portion of the ldap tree is simply a container.  This is not published on the internet and you will be the only one accessing it.  So you can call it absolutely anything you want.  I'd recommend the same thing dpiddy did.

---

