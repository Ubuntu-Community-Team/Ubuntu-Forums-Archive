---
title: "[SOLVED] grant users write access in ldap"
date: 2008-04-20
forum: Server Platforms
---

### Post by xyrer on 2008-04-20
Hi, I have deployed ldap to authenticate with squid and have made an ou for the mail directory, which I want to be apart.
I want to make an user who can add, edit and delete mail registries on that ou, but although I have tried everything I've seen on google, the user still has no rights to do it, here's the relevant config in slapd.conf
```
access to dn.subtree="ou=directory,dc=server" by dn="cn=edir,dc=server" write
```

---

### Post by geertn on 2008-04-21
Try putting the loglevel to 424 or -1 (extreme) for extensive debugging. 

I would start with 

access to * by dn="cn=edir,dc=server" write

To check if it matches your user. Check the logs and if this works, try working out the ou. If it doesn't, fix your dn statement:)

---

### Post by xyrer on 2008-06-23
It's funny, it works now, this is how it is posted on slapd.conf
```
access to dn.subtree="ou=directory,dc=server" by dn="cn=edir,dc=server" write by self write by users read by * auth
```
I solved it after reading this: [http://www.openldap.org/doc/admin22/slapdconfig.html#Access%20Control](http://www.openldap.org/doc/admin22/slapdconfig.html#Access%20Control)

---

