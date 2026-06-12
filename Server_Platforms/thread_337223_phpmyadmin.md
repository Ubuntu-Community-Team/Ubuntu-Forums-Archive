---
title: "phpmyadmin"
date: 2007-01-12
forum: Server Platforms
---

### Post by Ubuntuud on 2007-01-12
Hi,

I'm currently messing around with php and mysql, and now I'd like to use phpmyadmin.
But I don't know what username/password I should use and I get the following error:

```
Error
#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)

```

What do I need to do? Thanks in advance!

---

### Post by tturrisi on 2007-01-13
Can't you access phpmyadmin using the login:
username: root
password: don't enter a password, keep empty
Then once in phpmyadmin setup the priovledges & passwords.  That's how I do it on debian.

---

### Post by fearevilleet on 2007-01-16
I am having the same issue. I was unable to login in w/ root, using no password.  If you figured it out please post what you did. Thanks.

---

### Post by altonbr on 2007-01-30
That means that MySQL isn't configured properly.

Try running

```
$ sudo aptitude install mysql
```

and see if it wants to install any extra packages. phpMyAdmin should then be able to start.

Default username: root
Default password:

---

### Post by Brazen on 2007-01-30
also keep in mind that MySQL authentication is separate from your linux box'es normal authentication.  The MySQL install creates a root account by default, but this is completely different from the root account you use for logging into the console.

---

