---
title: "How to add an user or a group to sudoers with OpenLDAP"
date: 2013-10-27
forum: Server Platforms
---

### Post by webappl on 2013-10-27
I followed the following guide to install and configure LDAP for SUDO support on Ubuntu server 12.04
[http://ubuntuforums.org/showthread.php?t=1421998](http://ubuntuforums.org/showthread.php?t=1421998)

My question is how to add an user and a group to sudoers?

Thanks,

Alex

---

### Post by sandyd on 2013-10-27
> **webappl said:**
> I followed the following guide to install and configure LDAP for SUDO support on Ubuntu server 12.04
[http://ubuntuforums.org/showthread.php?t=1421998](http://ubuntuforums.org/showthread.php?t=1421998)

My question is how to add an user and a group to sudoers?

Thanks,

Alex

Is the group using the PosixGroup or GroupOfNames objectclass

If you are using posixGroup, just set the group name in the sudoers file

```

root@stargirl-bx2:~# id kathryn
uid=1001(kathryn) gid=502(global_administrators) groups=501(webhosting),502(global_administrators),504(gameserver_admins),506(gameserver_super_admins),507(redmine-108),508(mysql-109),509(webserver-114)
```

Take the group name (in this case, global_administrators), and put it in /etc/sudoers
```

%global_administrators ALL=(ALL:ALL) ALL
```

---

### Post by webappl on 2013-10-29
Thanks for you reply Sandyd.

I found a simple solution. When configuring sudo-ldap according to the guide in my first post, an entry with cn=%admin,ou=SUDOers,... has been added to the LDAP schema, which states that any user within group 'admin' will be sudoers. So we can simply add a group called 'admin' if it does not exist and then assign the user to admin group.

---

