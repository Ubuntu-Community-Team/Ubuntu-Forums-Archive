---
title: "MySQL Post Rotate error"
date: 2010-11-04
forum: Server Platforms
---

### Post by mistypotato on 2010-11-04
After running LogRotate on mysql I got this error....

[B][COLOR="Blue"]
error: error running shared postrotate script for /var/log/mysql.log /var/log/mysql/mysql.log /var/log/mysql/mysql-slow.log /var/log/mysql/QueryLog.txt /var/log/mysql/IsamLog.txt [/COLOR][/B]


And this is the Post Rotate script that caused it...

[B][COLOR="Blue"]test -x /usr/bin/mysqladmin || exit 0

# If this fails, check debian.conf! 
MYADMIN="/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf"
if [ -z "`$MYADMIN ping 2>/dev/null`" ]; then
# Really no mysqld or rather a missing debian-sys-maint user?
# If this occurs and is not a error please report a bug.
if ps cax | grep -q mysqld; then
exit 1
fi 
else
$MYADMIN flush-logs
fi[/COLOR][/B]



Anyone know what this means or what caused it?
user debian-sys-maint does exist and is mysql user and group with full permissions.
thx

---

