---
title: "MYSQL Problem"
date: 2012-02-26
forum: Server Platforms
---

### Post by firedragoneater on 2012-02-26
Hi,
I have managed to mess up MySql, I get error 1045 even though the password is right! I seem to have tried every way of changing it under the sun, but no luck! I've even tried purging MySql but one element needs the password!

Any help would be appreciated,
Jordan

---

### Post by firedragoneater on 2012-02-26
On attempting to stop mysql, I get this error.



Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mysql

---

