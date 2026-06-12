---
title: "How to enable mysql logging?"
date: 2010-10-26
forum: Server Platforms
---

### Post by osx on 2010-10-26
I'm trying to enable MySQL's General Query Log. I'm running version 5.0.51a of MySQL on Ubuntu 8.04 64-bit server.

The MySQL documentation found here [http://dev.mysql.com/doc/refman/5.0/en/query-log.html](http://dev.mysql.com/doc/refman/5.0/en/query-log.html) says to "start mysqld with the --log[=file_name] or -l [file_name] option".

But when I issue the following command: 

```
sudo /etc/init.d/mysql -l start
```

I get the following error message:
```

Usage: /etc/init.d/mysql start|stop|restart|reload|force-reload|status
```

Can anybody tell me how to enable MySQL logging since the above is not working?

Thanks.

---

### Post by Ryan Dwyer on 2010-10-26
That file is not mysqld. If I were you I'd try adding it to my.cnf under the [mysqld] section.

eg.
[mysqld]
log=/var/log/mysql.log

---

### Post by hawk2010 on 2010-10-27
First you have to stop the current mysql service by doing 
/etc/init.d/mysql stop

Then you need to restart the daemon as follows with the logging enabled

/usr/sbin/mysqld --log[=file_name]

but this won't be a permanent fix since on reboot it won't load the logging part. You may need to edit the my.cnf for that

---

