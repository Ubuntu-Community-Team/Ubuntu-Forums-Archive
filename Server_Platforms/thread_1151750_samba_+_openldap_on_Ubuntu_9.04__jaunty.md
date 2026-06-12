---
title: "samba + openldap on Ubuntu 9.04 / jaunty"
date: 2009-05-07
forum: Server Platforms
---

### Post by PoolSnoopy on 2009-05-07
Anyone ever succeeded in setting up samba + openldap on Ubuntu 9.04?
I'm stuck with an error when I try to add a windows client to the domain. On the windows side I get a 'User not found' error message.
On the server side I see this in the samba log file right after smbldap-useradd succeeded:
```

[2009/05/07 12:00:04,  3] passdb/pdb_interface.c:pdb_default_create_user(342)
  _samr_create_user: Running the command `sudo /usr/sbin/smbldap-useradd -w -t 5 "latvmie6$"' gave 0
[2009/05/07 12:00:04,  3] passdb/pdb_interface.c:pdb_default_create_user(359)
  pdb_default_create_user: failed to create a new user structure: NT_STATUS_NO_SUCH_USER

```
Anyone who got one step further?

---

### Post by ghen on 2009-05-19
nope, non functional for a newbie like me as well... I'm going back to 8.04 and try it since I have yet to complete an OpenLDAP install and authenticate to it.

---

### Post by lightnb on 2009-05-19
That usually happens when the server is trying to create the machine account, but fails.

Is this all of the message? It seems like more should come after the zero:
```

_samr_create_user: Running the command `sudo /usr/sbin/smbldap-useradd -w -t 5 "latvmie6$"' gave 0
```

Also, in smb.conf, post the lines you have for the add user script and add machine script.

---

### Post by PoolSnoopy on 2009-05-20
i don't have the log files anymore, but that was all after initiating the add machine script. the strange thing was, that samba and ldap managed to create a machine account in the ldap directory but right after this mentioned line I got an NT_USER_NOT_FOUND or similar error.
that caused the process of adding the machine to the domain to fail on the windows client side.

---

### Post by gpredrag on 2009-05-20
Not speaking from personal experience, but I've read somewhere that nscd running on ldap server can cause such problems. Try to stop it before adding computer account. 
Also in /etc/ldap.conf, is OU that contains computer accounts included in search base for user accounts?
Samba also can be used with ldapsam:editposix and ldapsam:trusted, so it (samba) can create appropriate ldap objects without help of any scripts.

---

