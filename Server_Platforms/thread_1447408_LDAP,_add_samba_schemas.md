---
title: "LDAP, add samba schemas"
date: 2010-04-05
forum: Server Platforms
---

### Post by Rokurosv on 2010-04-05
I've been trying to create a PDC with OpenLDAP and Samba to create a small test domain at work, and I've read a couple of tutorials, but I found out that the package in Karmic doesn't properly configure while installing and dpkg-reconfigure doesn't help either, so I've followed this guide [http://doc.ubuntu.com/ubuntu/serverguide/C/openldap-server.html](http://doc.ubuntu.com/ubuntu/serverguide/C/openldap-server.html)

along with this one 
[http://ohioloco.ubuntuforums.org/showthread.php?t=1184288](http://ohioloco.ubuntuforums.org/showthread.php?t=1184288)

And I managed to ge the base directory setup but when I try to populate the tree with the samba definitions it gives me a lot of errors saying 

```
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 106.
```

and it gives an error for each entry: Groups, Admins, Users, etc.

And at the bottom
```
Please provide a password for the domain root:
/usr/sbin/smbldap-passwd: user root doesn't exist
```

---

