---
title: "php mysql client"
date: 2009-05-22
forum: Server Platforms
---

### Post by amendrinos on 2009-05-22
hello,

I have installed mysql server 5.1.13 with the following command:

aptitude install mysql-server-5.1

and installed succesfully mysql 5.1.13

but there is no similar support for the php-mysql package. and the php-mysql client lib is still in version 5.0.x

How can I upgrade also php-mysql?

---

### Post by Vegan on 2009-05-24
You are better off installing the full LAMP stack with a fresh install of Ubuntu server. Just select the LAMP and it will all be installed properly with all the dependencies.

---

### Post by kvizz on 2009-05-24
> **Vegan said:**
> You are better off installing the full LAMP stack with a fresh install of Ubuntu server. Just select the LAMP and it will all be installed properly with all the dependencies.

maybe ```
sudo tasksel install lamp-server
``` would do the trick even on not fresh install?

---

### Post by Vegan on 2009-05-24
That does not always work in practice. Sometimes things are too mangled.

---

