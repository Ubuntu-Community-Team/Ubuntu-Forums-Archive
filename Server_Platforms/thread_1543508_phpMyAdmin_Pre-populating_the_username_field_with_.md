---
title: "phpMyAdmin Pre-populating the username field with strange characters"
date: 2010-08-01
forum: Server Platforms
---

### Post by cvandal on 2010-08-01
Hello,

Hopefully someone can help me out with this. I've installed the LAMP stack and straight after that, phpMyAdmin. When I browse to [http://mywebsite.com/phpmyadmin](http://mywebsite.com/phpmyadmin) the username field is pre-populated with strange characters... 7&#715;&#65533;_ to be exact.

Do anyone know why this is happening? I've tried installing phpMyAdmin using both apt-get and from the source and both provide the same outcome.

---

### Post by Ryan Dwyer on 2010-08-01
I think this happens when you had another installation of phpMyAdmin at the same address. Your browser probably stores the username in an encrypted cookie, so the new installation of phpMyAdmin doesn't decrypt it properly and you get garbage.

Erasing the username in the textbox and logging in should overwrite your cookie and fix it.

---

### Post by cvandal on 2010-08-01
> **Ryan Dwyer said:**
> I think this happens when you had another installation of phpMyAdmin at the same address. Your browser probably stores the username in an encrypted cookie, so the new installation of phpMyAdmin doesn't decrypt it properly and you get garbage.

Erasing the username in the textbox and logging in should overwrite your cookie and fix it.

That's it. Thanks for that :D

---

