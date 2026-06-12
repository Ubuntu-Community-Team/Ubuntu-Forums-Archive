---
title: "MySQL ERROR 2002 causing weird issues"
date: 2010-08-04
forum: Server Platforms
---

### Post by HittingSmoke on 2010-08-04
I started getting this error suddenly yesterday. MySQL was working before and I'm not sure exactly what I did when it broke.

```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

It comes with some other odd issues too. /var/run/mysqld/mysqld.sock doesn't exist. I tried creating it and restarting, but it disappears on each reboot.

Also, trying to restart the mysql server with *service mysql restart* doesn't work. It just moves the cursor down to a blank line until I press ctrl+C to get back to the bash prompt.

Any ideas?

---

