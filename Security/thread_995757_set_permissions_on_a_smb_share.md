---
title: "set permissions on a smb share"
date: 2008-11-28
forum: Security
---

### Post by b-boy on 2008-11-28
Hi guys i would like to know how to setup permissions on a smb share the permissions i would like is 

**users can write to folder but cannot move or delete anything in this folder only the owner should be able to delete and move items in folder**

---

### Post by hyper_ch on 2008-11-28
if they can "write" then the can also "delete".

---

### Post by b-boy on 2008-11-28
> **hyper_ch said:**
> if they can "write" then the can also "delete".

so theres no way ?

---

### Post by hyper_ch on 2008-11-28
not that I know of - although I have to admit that I don't know too much of samba.

---

### Post by Pom2122 on 2008-11-28
I'm a little rusty on perms, but if you set the folders perms to 1770 I think that would disallow anyone but the owner from deleting a file. I'm afraid it would still allow moving another users files though. I'd recursively chown that folder to (for example) root:users and then make sure that you and the users were members of the "users" group (or alternatively just create a new group just for samba users).
:)

---

### Post by liquid.silver on 2008-11-28
From my windows days i remember that permissions could be set to very specific scenarios, including what you've described, but i'm not sure how to do this in linux, sorry. I think it used ACLs.

EDIT: the share is hosted on a linux server i presume? if it's hosted on a windows server, i can help... but i doubt that's the situation.

---

### Post by cariboo on 2008-11-28
There is excellent documentation on Samba's web site. Have a look here:

[http://us1.samba.org/samba/](http://us1.samba.org/samba/)

I personally use:

[http://us1.samba.org/samba/docs/man/Samba-Guide/](http://us1.samba.org/samba/docs/man/Samba-Guide/)

quite a bit.

Jim

---

