---
title: "Why did 14.04 change web root directory?"
date: 2015-03-13
forum: Ubuntu, Linux and OS Chat
---

### Post by imotor on 2015-03-13
Upgrading from 12.04 to 14.04 completely fubared our web application. Among other changes, the apache web root (or document root) directory changed from /var/www/ to /var/www/html/.

Anyone know what the reasoning was behind this change?

---

### Post by cariboo on 2015-03-13
It was changed in Debian, and as Ubuntu is based on it, the change was made here too. See this [commitdiff]("http://anonscm.debian.org/gitweb/?p=pkg-apache/apache2.git;a=commitdiff;h=a6fd25c46f4e27ef2923977beb0c18e505176395;ds=sidebyside")

---

