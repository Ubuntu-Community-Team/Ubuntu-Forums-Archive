---
title: "Ldap auth fail"
date: 2007-05-17
forum: Server Platforms
---

### Post by lanux on 2007-05-17
Hi !

1. Sorry 4 my english :)
2. I think:I have an LDAP server, I can use it with phpldapadmin ( login, add,modify etc. ) 
I migrate basic,hosts,passwd,shadow,groups

I get this auth.log for #getent passwd | grep user
> May 17 23:54:37 ubuserver getent: nss_ldap: failed to bind to LDAP server ldap://127.0.0.1: Invalid credentials
May 17 23:54:37 ubuserver getent: nss_ldap: reconnecting to LDAP server...
May 17 23:54:37 ubuserver getent: nss_ldap: failed to bind to LDAP server ldap://127.0.0.1: Invalid credentials
May 17 23:54:37 ubuserver getent: nss_ldap: reconnecting to LDAP server (sleeping 1 seconds)...
May 17 23:54:38 ubuserver getent: nss_ldap: failed to bind to LDAP server ldap://127.0.0.1: Invalid credentials
May 17 23:54:38 ubuserver getent: nss_ldap: could not search LDAP server - Server is unavailable

when I want to login:
> May 18 00:00:37 ubuserver login[8607]: pam_ldap: ldap_simple_bind Can't contact LDAP server
May 18 00:00:39 ubuserver login[8607]: FAILED LOGIN (1) on 'tty1' FOR `oem', Authentication service cannot retrieve authentication info.

Any idea ?

---

### Post by nrgtek on 2007-08-23
I'm having the same can't bind error - anyone know why this is?

---

### Post by nrgtek on 2007-08-23
update on my situation. I still can't login and receive the:

```
Error
Could not bind to the LDAP server.

LDAP said: Undefined attribute type
Error number: 0x11 (LDAP_UNDEFINED_TYPE)
Description: The attribute type specified is invalid. 
```

I did however manage to login anonymously, but it puts it in read-only mode and I can't modify anything. I'm really at my wits end with getting this LDAP server setup.

---

### Post by panki on 2007-10-08
Same Problem Here, any help?

---

