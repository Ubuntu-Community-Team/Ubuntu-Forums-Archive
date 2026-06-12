---
title: "Lots of Apache activity in process list"
date: 2008-12-17
forum: Server Platforms
---

### Post by sipickles on 2008-12-17
Hi,

This is the output from ps -Af. Are all those apache entries correct?

```
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 Nov24 ?        00:00:00 init
root      5980 23647  0 19:21 ?        00:00:00 sshd: simon [priv]
simon     6118  5980  0 19:22 ?        00:00:00 sshd: simon@pts/0
simon     6119  6118  0 19:22 pts/0    00:00:00 -bash
www-data  9441 13612  0 19:24 ?        00:00:00 /usr/sbin/apache2 -k start
root     10027     1  0 08:32 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql    10067 10027  0 08:32 ?        00:00:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/r
root     10068 10027  0 08:32 ?        00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
www-data 13607 13612  0 14:01 ?        00:00:00 /usr/sbin/apache2 -k start
root     13612     1  0 11:07 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 13621 13612  0 11:07 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 13622 13612  0 11:07 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 13631 13612  0 19:27 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 15810 13612  0 11:09 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 19583 13612  0 11:12 ?        00:00:01 /usr/sbin/apache2 -k start
www-data 19752 13612  0 11:13 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 19755 13612  0 11:13 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 19756 13612  0 11:13 ?        00:00:00 /usr/sbin/apache2 -k start
simon    22190  6119  0 19:35 pts/0    00:00:00 ps -Af
syslog   23617     1  0 Nov24 ?        00:00:01 /sbin/syslogd -u syslog
root     23647     1  0 Nov24 ?        00:00:01 /usr/sbin/sshd
root     23838     1  0 Nov24 ?        00:00:00 /usr/sbin/vsftpd

```

I have restarted the apache server a few times with:

```
/etc/init.d/apache2 restart
```

Many thanks

Simon

---

### Post by cdenley on 2008-12-17
That looks normal. Nothing to worry about. By default, apache starts 5 server processes, and can have up to 10.

/etc/apache2/apache2.conf
```

# prefork MPM
[B]# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare[/B]
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
[B]    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10[/B]
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

```

---

### Post by sipickles on 2008-12-17
Thanks!

---

### Post by JeppeM on 2008-12-18
Depending on the load of the server, it can be much much more... Our main website-server normally has 30-50 apache proccesses running.

The idea behind apache is that there's one "main" process, which is the one owned by root in your example. That main proccess fires up children to handle requests, depending on the load... The more requests comming in to the server, the more children you'll normally have. The children have a shorter lifetime, as they're (normally) only allowed to serve x (1024 for example) amount of requests before they're shut down and a new one is started.

Hope that makes it a bit more understandable :)

---

### Post by sdnelson on 2008-12-18
You may want to run   apache2ctl status   which will tell you what activity if any is going on.

---

