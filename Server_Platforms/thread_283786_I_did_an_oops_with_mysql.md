---
title: "I did an oops with mysql"
date: 2006-10-24
forum: Server Platforms
---

### Post by involutaryhaxor on 2006-10-24
I made a mistake. I accidentally deleted the deb-sys-maint user or whatever it's called, is it possible to fix this problem, i get all sorts of errors when i shut down now. 

Please and thankyou

note: it still works, but i have a hunch that i should still keep it.

---

### Post by funkyade on 2006-10-24
what sort of errors? Post them here so we can have a look.

You could just back up all your databases and reinstall mysql then copy your databases back again (NOT the mysql one!!!!!) You will then need to flush privileges.

Can you access the mysql server via phpmyadmin or similar, if so just recreate the user...

!

---

### Post by involutaryhaxor on 2006-10-24
> **funkyade said:**
> what sort of errors? Post them here so we can have a look.

You could just back up all your databases and reinstall mysql then copy your databases back again (NOT the mysql one!!!!!) You will then need to flush privileges.

Can you access the mysql server via phpmyadmin or similar, if so just recreate the user...

!

this is the error:

```
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'

```

everything still works, but its not quite right to have error messages of the sort, in afraid that its gonna try to do some sort of maintenance thing and fail

what would i have to add to the new account

---

### Post by ejohney on 2006-10-25
try doing a sudo dpkg --reconfigure mysql-server-5.0

that should create the debian-sys-maint user. i think this is the same problem i had a while ago and if i remember right that fixed it right away. hope it works for you.

---

### Post by involutaryhaxor on 2006-10-25
i tried it, it was a completely silent operation (was it supposed to be?) and i looked through phpmyadmin and there was no such new user... i could completely reinstall the server, but i really don't want to do that

---

### Post by funkyade on 2006-10-25
> **involutaryhaxor said:**
> 
what would i have to add to the new account

I would assume global privileges, ie. root equivalent access. I don't have phpmyadmin nor docs for mysql5 to hand to confirm this however...

you could just try -
```
#> sudo aptitude reinstall mysql-server-5.0
```
this will preserve your exising databases and should recreate the user.

hth

---

### Post by involutaryhaxor on 2006-10-28
thankyou, its back.

---

