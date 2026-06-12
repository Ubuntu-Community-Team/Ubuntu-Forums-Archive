---
title: "ldap_bind: Invalid credentials (49)"
date: 2014-05-23
forum: Server Platforms
---

### Post by karaluh on 2014-05-23
I'm trying to set up Samba with LDAP following tutorials:
[https://help.ubuntu.com/10.04/serverguide/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/openldap-server.html)
to the "sudo ldapadd -Y EXTERNAL -H ldapi:/// -f backend.example.com.ldif" part, because I think I don't need it, right? Anyway, to this point everything works. When I try to configure Samba with LDAP following:
[https://help.ubuntu.com/10.04/serverguide/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/samba-ldap.html)
and everything works, to the "ldapadd -x -D cn=admin,cn=config -W -f /tmp/cn\=samba.ldif" part. When I try to execute this command I'm asked for LDAP password, and when I provide it (secret) I get "ldap_bind: Invalid credentials (49)" error. Why?

---

### Post by karaluh on 2014-05-28
Workarounded the issue by replacing ```
-x
``` with ```
-Y EXTERNAL -H ldapi:/// 
```only to hit another permissions error. This time when trying to import ldif by ```
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f aaa.ldif -c
``` I get ```
ldap_add: Insufficient access (50) additional info: no write access to parent
``` What can I do to fix it?

---

