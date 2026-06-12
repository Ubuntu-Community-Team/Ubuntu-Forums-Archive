---
title: "logrotate mysql password error"
date: 2021-02-06
forum: Server Platforms
---

### Post by spookybathtub on 2021-02-06
I'm running Ubuntu server 20.04 with MariaDB 10.3.25.  Today I noticed logrotate.service has failed because it doesn't have permission for mysql.
```

logrotate[741921]: error: 'Access denied for user 'root'@'localhost' (using password: NO)'
logrotate[741866]: error: error running shared postrotate script for '/var/log/mysql/mysql.log >
systemd[1]: logrotate.service: Main process exited, code=exited, status=1/FAILURE
```


[COLOR=#F2F2F2][FONT=Monaco][COLOR=#222222][FONT=Verdana]In /etc/logrotate.d/mysql-server I see the postrotate script is this
[/FONT][/COLOR][/FONT][/COLOR]
```

mysqladmin --defaults-file=/etc/mysql/debian.cnf --local flush-error-log \
              flush-engine-log flush-general-log flush-slow-lo

```

So I checked that file debian.cnf and its contents are this:
```
# Automatically generated for Debian scripts. DO NOT TOUCH![client]
host     = localhost
user     = root
password = 
socket   = /var/run/mysqld/mysqld.sock
[mysql_upgrade]
host     = localhost
user     = root
password = 
socket   = /var/run/mysqld/mysqld.sock
```

Where does this file come from?  I suppose I could enter the mysql root password here and call it a day, but I don't want it to be wiped out after a software update.  What's the right way to do this?  I've read on other forums where this file uses a user called "debian-sys-maint" with less privileges than root, which seems like a good idea.

---

