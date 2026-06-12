---
title: "mysqladmin not working"
date: 2009-05-06
forum: Server Platforms
---

### Post by _sluimers_ on 2009-05-06
I'm trying to follow this tutorial:

[http://workaround.org/articles/ispmail-etch/#step-2-create-the-database-and-user](http://workaround.org/articles/ispmail-etch/#step-2-create-the-database-and-user)

but I get this error message:

rogier@rogier-server:~$ mysqladmin password root2007
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'rogier'@'localhost' (using password: NO)'

What should I do?

---

### Post by ikonia on 2009-05-06
1.) make sure mysql is running as as erver
2.) use the -P password option - you need a password to authenticate your self as the root user


try not to follow generic guides, but use the ubuntu docs on [https://help.ubuntu.com](https://help.ubuntu.com)

---

