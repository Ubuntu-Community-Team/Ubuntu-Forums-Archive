---
title: "How to display users on Ubuntu Server"
date: 2007-01-21
forum: Server Platforms
---

### Post by JimTDI on 2007-01-21
Is there a way to display existing user accounts on the Ubuntu server - users that are created with adduser, and system users, and perhaps their permissions, group membership, etc.

I have searched in these forums, and on the web but can't seem to figure out how to do this.

---

### Post by Koybe on 2007-01-21
Just look in the files :

cat /etc/passwd
cat /etc/group

You'll get all you need.

---

### Post by jtc on 2007-01-21
```
cat /etc/passwd
```
username:password:user-id:default-group-id:real name:homedir:shell

```
cat /etc/group
```
groupname:password:group-id:list-of-users

You'll notice that the password-fields are most likely filled with "x". Nowdays passwords are instead stored in /etc/shadow. This is due to /etc/passwd and /etc/group having to be globally readable.

Of course, all this only goes if you store you accounts locally. With LDAP, NIS, etc it works a bit differently.

---

### Post by JimTDI on 2007-01-21
Thank you all - that gave me exactly what I needed!

---

### Post by fnjordy on 2007-01-22
> **jtc said:**
> Of course, all this only goes if you store you accounts locally. With LDAP, NIS, etc it works a bit differently.

These can usually be queried with the following:

> 
$ getent passwd
$ getent group


---

### Post by jtc on 2007-01-22
Didn't know about getent before. Quite usefull. Thank you.

---

