---
title: "LDAP and local group permissions"
date: 2017-09-19
forum: Server Platforms
---

### Post by e.ms on 2017-09-19
I have a problem or do not know where to start.

I have an LDAP server and a client in use. On my LDAP server I have created various groups and users.
**groups**
[LIST]
[*]admin
[*]user
[/LIST]

**user**
[LIST]
[*]user1
[*]user2
[/LIST]

If my users are not members of the group "user" or "admin", they can not log on to the client. For this I have the following file in the following file.
**/etc/security/access.conf**
```
+:user:ALL
+:admin:ALL
```

Now, however, I would like to prevent some users from accessing USB sticks, CD / DVD or floppy drives. There are some local groups, e.g. cdrom, plugdev or floppy which are provided for these permissions.

How do I remove an LDAP user from such a group? Or. how can I restrict an LDAP group? The LDAP group "user" is currently allowed to access everything.

---

### Post by ajgreeny on 2017-09-19
*Thread moved to **Server Platforms**.* which is more appropriate and a better fit.

---

### Post by e.ms on 2017-09-22
Does no one have an approach to this?

It is only an LDAP GROUP created. As far as I know, they do not have such permissions.
If I log on with a user to a client, only the LDAP USER is authenticated.
How can I restrict the local permissions for this LDAP USER?

---

