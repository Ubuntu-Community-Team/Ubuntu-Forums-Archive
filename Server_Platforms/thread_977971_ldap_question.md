---
title: "ldap question"
date: 2008-11-10
forum: Server Platforms
---

### Post by fouadk on 2008-11-10
hi everyone...

I have ubuntu desktops and ubuntu server and windows active directory and windows vistas...

I thought of creating an ldap server in order to create users for the linux machines...
Would an ldap server conflict with the active directory?
Cant i make linux machines use active directory for log in?
Do i still need nfs for users files?

Please help

Thanks in advance

---

### Post by pdwerryhouse on 2008-11-11
1) LDAP wouldn't conflict with the active directory server. You can run as many LDAP servers as you like on your network, they won't interfere with one another.

2) For active directory auth, have a look here: [http://www.linux.com/feature/40983](http://www.linux.com/feature/40983)

3) You'll still need NFS. LDAP will only handle accounts and authentication.

---

