---
title: "MariaDB systemctl status confusing me."
date: 2019-01-29
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2019-01-29
Everything is working fine but this is new. Ubuntu Xenial with mariadb-server. Just upgraded Kodi to Leia 18 from the ppa.

```
&#9679; mysql.service - LSB: Start and stop the mysql database server daemon
   Loaded: loaded (/etc/init.d/mysql; bad; vendor preset: enabled)
   Active: active (running) since Tue 2019-01-29 13:17:42 MST; 1min 20s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 1584 ExecStart=/etc/init.d/mysql start (code=exited, status=0/SUCCESS)
    Tasks: 43
   Memory: 199.4M
      CPU: 22.140s
   CGroup: /system.slice/mysql.service
           &#9500;&#9472;1765 /bin/bash /usr/bin/mysqld_safe
           &#9500;&#9472;1972 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.soc
           &#9492;&#9472;1973 logger -t mysqld -p daemon error


Jan 29 13:17:41 megalith mysqld[1973]: 190129 13:17:41 [Note] InnoDB: Waiting for purge to start
Jan 29 13:17:41 megalith mysqld[1973]: 190129 13:17:41 [Note] InnoDB:  Percona XtraDB (http://www.percona.com) 5.6.39-83.1 started; log sequence number 153358006
Jan 29 13:17:41 megalith mysqld[1973]: 190129 13:17:41 [Note] Plugin 'FEEDBACK' is disabled.
Jan 29 13:17:42 megalith mysqld[1973]: 190129 13:17:42 [Note] Server socket created on IP: '0.0.0.0'.
Jan 29 13:17:42 megalith mysqld[1973]: 190129 13:17:42 [Note] /usr/sbin/mysqld: ready for connections.
Jan 29 13:17:42 megalith mysqld[1973]: Version: '10.0.36-MariaDB-0ubuntu0.16.04.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Ubuntu 16.04
Jan 29 13:17:42 megalith mysql[1584]:    ...done.
Jan 29 13:17:42 megalith systemd[1]: Started LSB: Start and stop the mysql database server daemon.
Jan 29 13:17:43 megalith /etc/mysql/debian-start[2140]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Jan 29 13:17:43 megalith /etc/mysql/debian-start[2156]: Checking for insecure root accounts.
```

I'm confused about the lines that have [Note] in them. They are red which usually isn't a good thing. Not sure if I should worry. Like I said, the database seems to be functioning, Kodi has all my media like it did before the upgrade. Maybe it's normal and I never noticed? Just curious.

---

