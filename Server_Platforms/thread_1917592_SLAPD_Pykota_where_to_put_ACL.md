---
title: "SLAPD Pykota where to put ACL?"
date: 2012-01-30
forum: Server Platforms
---

### Post by AqadAbdelaziz on 2012-01-30
Hi,

I've got a problem with pykota, a software to limit printer usage for users. 
I have to integrate directives and acl in my ldap server (oneiric 11.10)  but i don't know where and don't want to make mistakes.

ACL 
```
 access to dn.subtree="ou=PyKota,dc=example,dc=com"
               by dn="cn=pykotaadmin,dc=example,dc=com" write

        access to dn.subtree="ou=People,dc=example,dc=com"
               by dn="cn=pykotaadmin,dc=example,dc=com" write

        access to dn.subtree="ou=Groups,dc=example,dc=com"
               by dn="cn=pykotaadmin,dc=example,dc=com" write

```directives
```

limits dn="cn=pykotaadmin,dc=example,dc=com" size.soft=-1 size.hard=soft
       limits dn="cn=pykotauser,dc=example,dc=com" size.soft=-1 size.hard=soft

```
Thanks a lot.

---

