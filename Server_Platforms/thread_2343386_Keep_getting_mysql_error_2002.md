---
title: "Keep getting mysql error 2002"
date: 2016-11-15
forum: Server Platforms
---

### Post by micahpage on 2016-11-15
I keep getting mysql errors on my MyBB forum ran on an ubuntu server. 



[IMG]https://community.mybb.com/attachment.php?aid=37793[/IMG]

sock exists
```
metulburr /var/run/mysqld $ ls
mysqld.pid  mysqld.sock
```

and the only way to fix it seems to be to restart mysql
```
sudo /etc/init.d/mysql restart
```

So i made a cron job for root
```
*/5 * * * * /etc/init.d/mysql restart


```
and started cron.

but this doesnt seem to be the best solution. What is the root cause of the mysql error?

Als the respawn directive is in conf file
/etc/init/mysql.conf
```

# MySQL Service
 
description     "MySQL Server"
author          "Mario Limonciello <superm1@ubuntu.com>"
 
start on runlevel [2345]
stop on starting rc RUNLEVEL=[016]
 
respawn
respawn limit 2 5
 
env HOME=/etc/mysql
umask 007
 
# The default of 5 seconds is too low for mysql which needs to flush buffers
kill timeout 300
 
pre-start script
    ## Fetch a particular option from mysql's invocation.
    # Usage: void mysqld_get_param option
    mysqld_get_param() {
      /usr/sbin/mysqld --print-defaults \
        | tr " " "\n" \
        | grep -- "--$1" \
        | tail -n 1 \
        | cut -d= -f2
    }
 
    # priority can be overriden and "-s" adds output to stderr
    ERR_LOGGER="logger -p daemon.err -t /etc/init/mysql.conf -i"
 
    #Sanity checks
    [ -r $HOME/my.cnf ]
    [ -d /var/run/mysqld ] || install -m 755 -o mysql -g root -d /var/run/mysqld
    /lib/init/apparmor-profile-load usr.sbin.mysqld
 
    # check for diskspace shortage
    datadir=`mysqld_get_param datadir`
    BLOCKSIZE=`LC_ALL=C df --portability $datadir/. | tail -n 1 | awk '{print $4}'`
    if [ $BLOCKSIZE -le 4096 ] ; then
      echo "$0: ERROR: The partition with $datadir is too full!" >&2
      echo "ERROR: The partition with $datadir is too full!" | $ERR_LOGGER
      exit 1
    fi
end script
 
exec /usr/sbin/mysqld
 
post-start script
   for i in `seq 1 30` ; do
        /usr/bin/mysqladmin --defaults-file="${HOME}"/debian.cnf ping && {
            exec "${HOME}"/debian-start
            # should not reach this line
            exit 2
        }
        statusnow=`status`
        if echo $statusnow | grep -q 'stop/' ; then
            exit 0
        elif echo $statusnow | grep -q 'respawn/' ; then
            exit 1
        fi
        sleep 1
    done
    exit 1
end script

```

---

