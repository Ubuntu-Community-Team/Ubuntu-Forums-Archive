---
title: "PHP shows 500 Server Error instead of complete error reports"
date: 2010-12-26
forum: Server Platforms
---

### Post by Eberk89 on 2010-12-26
Hi
I'm running Ubuntu 10.04 with a complete LAMP installation (for local developement purpose).

Everything is OK (I installed phpMyAdmin without problems) except for one big problem: php shows 500 server internal error instead of a complete error report.

I tried editing php.ini and in-script runtime configuration but nothing changed.

Can anybody help me? I'm really confused and losing a lot of (useful) time!!

thanks

---

### Post by aceofspades686 on 2010-12-26
500 Internal Server Error is actually a full error report coming from Apache, typically meaning that something is misconfigured within your apache2 installation.

If you could, post your error logs from /var/log/apache2/error.log and we may be able to help pinpoint what's wrong.  To display these logs:
```
cat /var/log/apache2/error.log
```

EDIT:
Also, a bit more information might be useful.  Does this happen on all websites or just one? If only one specific one, are there any circumstances which specifically seem to cause this?

---

