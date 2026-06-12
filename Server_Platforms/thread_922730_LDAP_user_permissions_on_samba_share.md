---
title: "LDAP user permissions on samba share"
date: 2008-09-17
forum: Server Platforms
---

### Post by shizakapayou on 2008-09-17
I'm running an Ubuntu OpenLDAP server with Samba.  I'm trying to get it setup as a file server, but I need some help with my samba shares.

As an example, I have a folder called test.  I want the LDAP group Domain Admins to have full control, but Domain Users should have read-only, and the group Domain Test should have no access.

I've made several attempts, including something like below:

```

[test]
        path = /home/test
        write list = @Domain Admins
        read list = @Domain Users
        browseable = yes

```

with no luck.  I can see the share but no one can write to it.

When I create the folder test, this is the result of ls -la:
```
drwxr-xr-x  2 root          root           4096 2008-09-17 14:49 test

```

I've seen plenty on google about using Samba groups in smb.conf, but I haven't found anything about LDAP groups, which I assume is handled different.  Suggestions?

---

### Post by shizakapayou on 2008-09-18
Bump - anyone?

---

### Post by ahardo on 2009-01-22
i got the same problem, every users on my server can open, list and write every folder on my server, what is the problem bout the permision can someone Help me ? i using LDAP and samba, on ubuntu 7.10

thanks before

---

