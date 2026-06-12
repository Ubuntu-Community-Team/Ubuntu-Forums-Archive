---
title: "Using monit for services with no pid"
date: 2010-09-08
forum: Server Platforms
---

### Post by Jay2001 on 2010-09-08
It would seem MySQL and VSFTP no longer create pid files and monit requires a pid file to work. Is there any way to force MySQLD and VSFTPD to use pid files or am I out of luck?

---

### Post by yota on 2010-09-08
You can tell mysql to create a pid file by adding a configuration file (i.e. pid.cnf in /etc/mysql/conf.d) which has to contain
```

[mysqld]
pid-file = /var/run/mysqld/mysqld.pid

```
For vsftp I suppose that you'll have to tweak the init script and include the pidfile creation there...

See [http://mmonit.com/wiki/Monit/FAQ](http://mmonit.com/wiki/Monit/FAQ) for examples about this approach.

---

### Post by Jay2001 on 2010-09-08
Part 1 of your solution has worked beautifully, thanks. Looking into part 2 now.

---

### Post by Jay2001 on 2010-09-09
Hmmm, I'm now running into some other niggles with Monit, other than Nagios does anyone have a recommendation for server monitoring?

---

