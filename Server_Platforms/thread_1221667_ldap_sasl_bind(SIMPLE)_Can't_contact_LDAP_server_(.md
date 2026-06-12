---
title: "ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)"
date: 2009-07-24
forum: Server Platforms
---

### Post by IMadhavan on 2009-07-24
Hi
I had configured ldap server in ubuntu 9.04
when i searched my dn name i got this error 
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

Can anyone help me?

---

### Post by yuefei on 2009-07-30
i've got the same pb.
did u fix it?
if u did, how?
much thx

---

### Post by jokker on 2009-08-12
same issue here following [this]("http://wiki.samba.org/index.php/Samba4/HOWTO/Ubuntu_Server_9.04") guide
the error happens when typing this command in the Provisioning section:
```
ldapsearch -x -b  -s base '(objectclass=*)' namingContexts -H ldapi://%2Fusr%2Flocal%2Fsamba%2Fprivate%2Fldap%2Fldapi
```
Any help would be greatly appreciated.
thanks a lot.

---

