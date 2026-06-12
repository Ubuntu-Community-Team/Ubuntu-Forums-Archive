---
title: "Mysql Second Instance not starting on boot"
date: 2011-11-23
forum: Server Platforms
---

### Post by neomaximus2k on 2011-11-23
Hey guys, need some help on this once recently installed Ubuntu 11.10 after our replication server died a horrible gruesome death, now I have a single instance of mysql running on port 3306 and have setup another instance running on port 3307 which will be the replication server (reason for this is we are using the same machine as an in-house development platform and off-site production replication backup)

I followed the instructions below to get the two instances running and they do not a problem however I can't figure out how to get the system to auto start the second instance on boot-up

[http://www.ducea.com/2009/01/19/running-multiple-instances-of-mysql-on-the-same-machine/]("http://www.ducea.com/2009/01/19/running-multiple-instances-of-mysql-on-the-same-machine/")


I have copied the mysql.conf in the init folder to run as mysql-rep.conf and changed the paths as shown below

```
# MySQL Service

description     "MySQL Server"
author          "Bob Builder <bobthebuilder@bobthebuilder.com>"

start on (net-device-up
          and local-filesystems
          and runlevel [2345])
stop on runlevel [016]

respawn

env HOME=/etc/mysql-rep
umask 007

# The default of 5 seconds is too low for mysql which needs to flush buffers
kill timeout 300

pre-start script
    #Sanity checks
    [ -r $HOME/my.cnf ]
    [ -d /var/run/mysqld ] || install -m 755 -o mysql -g root -d /var/run/mysqld
    /lib/init/apparmor-profile-load usr.sbin.mysqld
    LC_ALL=C BLOCKSIZE= df --portability /var/lib/mysql-rep/. | tail -n 1 | awk '{ exit ($4<4096) }'
end script

exec /usr/sbin/mysqld

post-start script
   for i in `seq 1 30` ; do
        /usr/bin/mysqladmin --defaults-file="${HOME}"/debian.cnf ping && {
            exec "${HOME}"/debian-start
            # should not reach this line
            exit 2
        }
        sleep 1
    done
    exit 1
end script
```

the my.cnf for mysql-rep
```
[client]
port            = 3307
socket          = /var/run/mysqld/mysqld-rep.sock

[mysqld_safe]
socket          = /var/run/mysqld/mysqld-rep.sock
nice            = 0

[mysqld]
user            = mysql
socket          = /var/run/mysqld/mysqld-rep.sock
port            = 3307
basedir         = /usr
datadir         = /var/lib/mysql-rep
tmpdir          = /tmp
skip-external-locking
#bind-address           = 127.0.0.1
key_buffer              = 16M
max_allowed_packet      = 16M
thread_stack            = 192K
thread_cache_size       = 8

myisam-recover         = BACKUP
query_cache_limit       = 1M
query_cache_size        = 16M

log_error                = /var/log/mysql-rep/error.log

#server-id              = 1
expire_logs_days        = 10
max_binlog_size         = 100M

[mysqldump]
quick
quote-names
max_allowed_packet      = 16M

[mysql]
#no-auto-rehash # faster start of mysql but no tab completition

[isamchk]
key_buffer              = 16M

!includedir /etc/mysql/conf.d/
```

debian.cnf
```
[client]
host     = localhost
user     = debian-sys-maint
password = REMOVED
socket   = /var/run/mysqld/mysqld-rep.sock
[mysql_upgrade]
host     = localhost
user     = debian-sys-maint
password = REMOVED
socket   = /var/run/mysqld/mysqld-rep.sock
basedir  = /usr
```

Any and all help greatly appreciated.

---

### Post by Vegan on 2011-11-23
AFAIK MySQL only listens on one port

Best bet is to find another machine or VM and use that for replication purposes

---

### Post by neomaximus2k on 2011-11-23
Vegan, you can setup multiple instances to listen on multiple ports, the replication server and standard server are both working together just not running at startup

---

### Post by cj13579 on 2011-11-23
You could write a simple bash script to launch you mysqld instance (call if foo):

```

#!/bin/bash

mysqld --config /etc/mysql-rep.conf

```

and then place it into /etc/init.d and then run:

```
update-rc.d foo defaults
```

---

### Post by neomaximus2k on 2011-11-23
Hi CJ,
Thats what I figured but its upstart and it jsut doesn't seem to work.

Ideally need control for start, stop and restart 

I tried the following but it just sits there!

```
#!/bin/sh
# Begin /etc/init.d/mysql

source /etc/init.d/functions

case "$1" in
        start)
                echo -n "Starting mysql..."
                /usr/bin/mysqld_safe --defaults-file=/etc/mysql-rep/my.cnf &
                evaluate_retval
                ;;

        stop)
                echo -n "Stopping mysqld..."
                kill `cat /var/run/mysqld/mysqld-rep.pid`
                evaluate_retval
                ;;

        restart)
                $0 stop
                /usr/bin/sleep 1
                $0 start
                ;;

        status)
                statusproc /usr/bin/mysqld
                ;;

        *)
                echo "Usage: $0 {start|stop|restart|status}"
                exit 1
        ;;

esac
```

---

### Post by neomaximus2k on 2011-11-24
Thanks CJ, needed to make a few changes but got there in the end!

```


#!/bin/sh
# Begin /etc/init.d/mysql

#source /etc/init.d/functions

case "$1" in
        start)
                echo -n "Starting mysql..."
                /usr/bin/mysqld_safe --defaults-file=/etc/mysql-rep/my.cnf >/dev/null 2>&1  &
                ret=$?
                ;;

        stop)
                echo -n "Stopping mysqld..."
#               kill `cat /var/run/mysqld/mysqld-rep.pid`
                mysqladmin -S /var/run/mysqld/mysqld-rep.sock shutdown > /dev/null 2>&1
                ret=$?
                ;;

        restart)
                $0 stop
                /usr/bin/sleep 1
                $0 start
                ;;

        status)
                statusproc /usr/bin/mysqld
                ;;

        *)
                echo "Usage: $0 {start|stop|restart|status}"
                exit 1
        ;;

esac

exit $?


```

---

### Post by cj13579 on 2011-11-24
Good stuff, glad you managed to get it sorted.

---

