---
title: "OpenLDAP Server, LDAP replication Invalid syntax error"
date: 2009-02-08
forum: Server Platforms
---

### Post by ezimir on 2009-02-08
Hello. I'm begginer with ubuntu server (currently trying 8.10).

I'm following [Ubuntu Server Guide > Network Authentication > OpenLDAP Server]("https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html") guide. 

In LDAP replication section 
```
ldapmodify -x -D cn=admin,cn=config -W -f syncrepl_cn-config.ldif
```
gives
```
Enter LDAP Password:
modifying entry "cn=config"

adding new entry "olcOverlay=syncprov,olcDatabase={0}config,cn=config"
ldap_add: Invalid syntax (21)
        additional info: objectClass: value #1 invalid per syntax
```

My google search on problem returned help like: problems with trailing spaces, tabs, mistyping. I just copy pasted the syncrepl_cn-config.ldif file data from the guide, so i believe it's not this kind of problem.

Anyone has idea what might be wrong here?

---

### Post by Mers2009 on 2009-06-20
[LEFT]Hi ezimir I'm exacly with the same problem. Did you find out the reason for this error?

Best regards
[/LEFT]

---

