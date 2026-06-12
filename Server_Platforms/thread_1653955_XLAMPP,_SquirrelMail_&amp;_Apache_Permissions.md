---
title: "XLAMPP, SquirrelMail &amp; Apache Permissions"
date: 2010-12-27
forum: Server Platforms
---

### Post by jago25_98 on 2010-12-27
I want to use XLAMPP, the package for Apache/PHP,MySQL etc that sits in /opt completely separate from the Ubuntu packages. 

However, the SquirrelMail package is set for user `nobody` whereas XLAMPP is expecting user `www-data`

Otherwise I get when using SquirrelMail:

[I]Error opening ../config/default_pref
Could not create initial preference file!
/var/lib/squirrelmail/data/ should be writable by user nobody
Please contact your system administrator and report this error.[/I]

What can I change to use XLAMPP alongside the official Apache package? 

Surely I need to change something in XLAMPP?

---

