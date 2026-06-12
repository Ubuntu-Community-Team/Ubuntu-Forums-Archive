---
title: "[SOLVED] Can't connect with anyone but root"
date: 2008-10-17
forum: Server Platforms
---

### Post by Bluebell392 on 2008-10-17
Hello,

I can't connect to a local MySQL with anyone but the root user. The error I get is: ```
Access denied for user 'x'@'localhost' (using password: YES)
``` where x is a user name. I add the users through phpMyadmin, then reload the privileges. 

Any ideas?

---

### Post by cdenley on 2008-10-17
Login to mysql as root, then grant permissions for whatever user's you want.
```

grant all on mydatabase.* to 'x'@'localhost' identified by 'mypass';

```

---

### Post by cariboo on 2008-10-17
I use the following two lines to create another mysql user:

```
grant all privileges on *.* to test@'localhost' identified by 'testpass' with grant option;
```

and

```
grant all privileges on *.* to test@'%' identified by 'testpass' with grant option;
```

This creates a user with full privileges. Use both commands if you want to remotely access the db.

Jim

---

### Post by cdenley on 2008-10-17
> **cariboo907 said:**
> I use the following two lines to create another mysql user:

```
grant all privileges on *.* to test@'localhost' identified by 'testpass' with grant option;
```

and

```
grant all privileges on *.* to test@'%' identified by 'testpass' with grant option;
```

This creates a user with full privileges. Use both commands if you want to remotely access the db.

Jim

I wouldn't recommend connecting as a user with grant permission or access to the system database from a web script. I also wouldn't recommend giving any access to remote users, unless your webserver and your database server are seperate servers.

---

