---
title: "Ubuntu &amp; Joomla:  SQL problem"
date: 2010-03-10
forum: Server Platforms
---

### Post by ibetimpostingforhelp on 2010-03-10
Yesterday I had installed the LAMP stack and Joomla for Karmic.  Had everything working fine; I got through the Joomla installation and called it a day.  After one restart, I attempted to run Joomla again.  I noticed Apache and MySQL were not started, so no problem I started both:

```
/etc/init.d/apache2 start

/etc/init.d/mysql start
```

Both scripts reported no errors.

I try to access Joomla using [http://localhost/joomla/](http://localhost/joomla/)

I get the following error.

> Database Error: Unable to connect to the database:The MySQL adapter "mysql" is not available.

What?

I tested to see if I can login to mysql with user root and the password, it works fine.  Joomla uses root to access mysql as well, as I specified during the install.  It worked last night.  Am I missing something?

Thanks.

---

