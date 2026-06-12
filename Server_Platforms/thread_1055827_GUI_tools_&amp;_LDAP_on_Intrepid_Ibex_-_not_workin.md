---
title: "GUI tools &amp; LDAP on Intrepid Ibex - not working well"
date: 2009-01-31
forum: Server Platforms
---

### Post by pauwl on 2009-01-31
I've installed LDAP on Intrepid.

I can add users & groups if I do the following:

```
sudo /etc/init.d/slapd stop
```
I then create an LDIF file.
```
sudo slapadd -l init1.ldif
```
then I restart the deamon with
```
sudo /etc/init.d/slapd start
```

This all works OK. Users are added just fine.
If however I try using LUNA or 'directory administrator' or any of the other GUI's I get an error of 'Insufficient Access' or the like.

I am connecting with the 'cn=admin,dc=mydomain,dc=com' account, so I think it *should* work.

Any ideas? It doesn't seem ideal needing to stop/start the deamon to add users.

---

