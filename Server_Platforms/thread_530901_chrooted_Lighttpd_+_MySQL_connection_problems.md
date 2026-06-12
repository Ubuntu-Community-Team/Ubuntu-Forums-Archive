---
title: "chrooted Lighttpd + MySQL connection problems"
date: 2007-08-21
forum: Server Platforms
---

### Post by gaten on 2007-08-21
OK, this is driving me nuts. I've got 

```
lighttpd-1.4.13 
mysql 5.0
PHP 5
```

All chrooted. PHP works fine, and mysql worked fine OUTSIDE the chroot. Now I've got this error:
```
[20-Aug-2007 19:55:39] PHP Warning:  mysql_query() [<a href='function.mysql-query'>function.mysql-query</a>]: Lost connection to MySQL server during query in /home/lighttpd/gaten/db.php on line 9
[20-Aug-2007 19:55:39] PHP Warning:  mysql_query() [<a href='function.mysql-query'>function.mysql-query</a>]: A link to the server could not be established in /home/lighttpd/gaten/db.php on line 9

```


So it can't connect to the server, and it gives me very little information to go on. Here's the relevant parts of my config files (all within the chroot):

NOTE: it should be noted that there are two different chroots here, one for lighttpd and PHP, and one for mysql. The mysql config files are in the mysql chroot obviously, in **/www/mysql**.  I have also made a hard link with the mysql socket from /www/mysql/tmp/mysql.sock to /www/tmp/mysql.sock. This should work, but I think it may be the problem.

[U][B]LIghttpd Chroot

[/B][/U]/etc/php5/cgi/php.ini
```
mysql.default_socket = "/tmp/mysql.sock"
mysqli.default_socket = "/tmp/mysql.sock"
```

[U][B]Mysql Chroot

[/B][/U]/etc/my.cnf
```
[mysqld]
socket = /tmp/mysql.sock
```


Without a more specific error message, I simply don't know whats going on. Any ideas?

And yes, both mysql.sock's exist.

---

### Post by a9k on 2007-08-21
1) Check permissions on the sockets.

2) Check PHP can find the socket from its chroot jail by using "su" to be the PHP user in its chroot jail. Then try mysql access while in jail.

3) It could be a library that isn't accessible in the jail causes the problem.

You could just be looking /tmp/ being in two different places for the two jails. So /home/php/tmp and /home/mysql/tmp might not be the same directory.

---

### Post by gaten on 2007-08-21
> 1) Check permissions on the sockets.Both sockets are owned by user mysql and have 777 permissions, and the tmp dir is owned by root and has 777 permissions.

>  2) Check PHP can find the socket from its chroot jail by using "su" to be the PHP user in its chroot jail. Then try mysql access while in jail.Good idea, but didn't fail (like you would want it to in this situation). I couldn't su to the www-data user (which lighttpd runs as) due to a "su: pam_start: error 26" (obviously some of the correct config files weren't copied into the chroot). But as root, I could access mysql via /tmp, and see everything fine. 

>  3) It could be a library that isn't accessible in the jail causes the problem.How can I check for this? Shouldn't mysql throw an error of some sort?

>  You could just be looking /tmp/ being in two different places for the two jails. So /home/php/tmp and /home/mysql/tmp might not be the same directory.Yes, there are two socket locations, but I hard link them with this script on mysql startup:
```

#!/bin/sh

CHROOT_MYSQL=/www/mysql
CHROOT_PHP=/www/
SOCKET=tmp/mysql.sock
MYSQLD=/usr/local/mysql/libexec/mysqld
PIDFILE=/usr/local/mysql/var/`hostname`.pid
CHROOTUID=/usr/bin/chrootuid

echo -n "mysql..."

case "$1" in
start)
        rm -rf ${CHROOT_PHP}/${SOCKET}
        nohup ${CHROOTUID} ${CHROOT_MYSQL} mysql ${MYSQLD} >/dev/null 2>&1 &
        sleep 5 && ln ${CHROOT_MYSQL}/${SOCKET} ${CHROOT_PHP}/${SOCKET}
        echo "started."
        ;;
stop)
        kill `cat ${CHROOT_MYSQL}/${PIDFILE}`
        rm -rf ${CHROOT_MYSQL}${SOCKET}
        echo "stopped."
        ;;
*)
        echo ""
        echo "Usage: `basename $0` {start|stop}" >&2
        exit 64
        ;;
esac

exit 0

```Thanks for the reply, I'll keep pecking away at it and see what I get.
As you can see it hard links the sockets between the chroots.

---

