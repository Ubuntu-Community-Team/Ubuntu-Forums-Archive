---
title: "apache2"
date: 2006-08-23
forum: Server Platforms
---

### Post by string on 2006-08-23
Hey, I apt-get-installed apache2.
But sudo /etc/init.d/apache2 start doesn't work.
sudo /etc/init.d/apache2 stop works.
But the only way to start it is sudo apache2 ... that's weird.

Also, what should I do to have it started at boot ? Thanks !

---

### Post by henrrrik on 2006-08-23
Sounds like a configuration problem. Check your logs.

---

### Post by az on 2006-08-23
> **string said:**
> Hey, I apt-get-installed apache2.
But sudo /etc/init.d/apache2 start doesn't work.
sudo /etc/init.d/apache2 stop works.
But the only way to start it is sudo apache2 ... that's weird.

Also, what should I do to have it started at boot ? Thanks !

It starts when you install it and at boot.

What happens when you browse localhost after you boot up?

---

### Post by string on 2006-08-23
Well, I cannot reboot now.
But when I start it with sudo apache2, it works 100% fine : subversion repository works, personnal directorues also, localhost shows what is should.

Also, as I said : sudo /etc/init.d/apache2 stop works but not start.

---

