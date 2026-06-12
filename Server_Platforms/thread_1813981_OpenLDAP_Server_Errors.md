---
title: "OpenLDAP Server Errors"
date: 2011-07-28
forum: Server Platforms
---

### Post by d.justins on 2011-07-28
I have been attempting to install and configure OpenLDAP following the 10.04 official guide located here:
[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)

When "Setting Up ACL" i use the ldapsearch utility with the command:

```
ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase=hdb olcAccess
```

I get an 

```
ldap_bind: Invalid credentials(49)
```

error. I know i have followed the guide very specifically and completely. 

According to the guide, you create a user cn=admin,dc=example,dc=com
However, you don't create one with cn=admin,cn=config base. 

I have tried binding with the cn=admin,dc=example,dc=com however, i get a 

```
No Such Object (32)
```

Error. 

Furthermore, is this really the best group of guides to getting OpenLDAP and Samba to work together?

---

