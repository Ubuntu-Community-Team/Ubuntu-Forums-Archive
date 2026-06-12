---
title: "is 1GB too little for our server"
date: 2016-11-18
forum: Server Platforms
---

### Post by micahpage on 2016-11-18
We have been having a lot of problems with MySQL crashes. And by crashes i mean they get fixed just by refreshing the browser. I made a cron job to restart mysql every 5 minutes because once the mysql would not fix itself. 

The errors are different, not always the same one, sometimes a 2002, sometimes a 2006 error. Sometimes you can get the same mysql error doing different things on the server. Its hard to pinpoint and reproduce the errors, as they always seem to change.

1) Based on this is there anything i can do to fix these mysql errors?
2) Is 1GB RAM too little for our forum? link to it-> [www.python-forum.io]("http://www.python-forum.io/") (its not uncommon to have 10 members actively engaged in conversation)

the server is a VPS with 1GB RAM 30GB HDD. 

all below is just different info as i am not sure what info is needed to target the cause.




i edited the my.cnf file to beef up in attempt to fix mysql but this doesnt seem to have worked.
```


[COLOR=#669933]*#*[/COLOR][COLOR=#669933]*# The MySQL database server configuration file.*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# You can copy this to one of:*[/COLOR]
[COLOR=#669933]*# - "/etc/mysql/my.cnf" to set global options,*[/COLOR]
[COLOR=#669933]*# - "~/.my.cnf" to set user-specific options.*[/COLOR]
[COLOR=#669933]*# *[/COLOR]
[COLOR=#669933]*# One can use all long options that the program supports.*[/COLOR]
[COLOR=#669933]*# Run program with --help to get a list of available options and with*[/COLOR]
[COLOR=#669933]*# --print-defaults to see which it would actually understand and use.*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# For explanations see*[/COLOR]
[COLOR=#669933]*# http://dev.mysql.com/doc/mysql/en/server-system-variables.html*[/COLOR]

[COLOR=#669933]*# This will be passed to all mysql clients*[/COLOR]
[COLOR=#669933]*# It has been reported that passwords should be enclosed with ticks/quotes*[/COLOR]
[COLOR=#669933]*# escpecially if they contain "#" chars...*[/COLOR]
[COLOR=#669933]*# Remember to edit /etc/mysql/debian.cnf when changing the socket location.*[/COLOR]
[client]
port        = 3306
socket        = /var/run/mysqld/mysqld.sock

[COLOR=#669933]*# Here is entries for some specific programs*[/COLOR]
[COLOR=#669933]*# The following values assume you have at least 32M ram*[/COLOR]

[COLOR=#669933]*# This was formally known as [safe_mysqld]. Both versions are currently parsed.*[/COLOR]
[mysqld_safe]
socket        = /var/run/mysqld/mysqld.sock
nice        = 0

[mysqld]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# * Basic Settings*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
user        = mysql
pid-[COLOR=#00AAAA]file[/COLOR]    = /var/run/mysqld/mysqld.pid
socket        = /var/run/mysqld/mysqld.sock
port        = 3306
basedir        = /usr
datadir        = /var/lib/mysql
tmpdir        = /tmp
lc-messages-[COLOR=#00AAAA]dir[/COLOR]    = /usr/share/mysql
skip-external-locking
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# Instead of skip-networking the default is now to listen only on*[/COLOR]
[COLOR=#669933]*# localhost which is more compatible and is not less secure.*[/COLOR]
bind-address        = 127.0.0.1
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# * Fine Tuning*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
key_buffer        = 256M
max_allowed_packet    = 128M
thread_stack        = 192K
thread_cache_size       = 8
[COLOR=#669933]*# This replaces the startup script and checks MyISAM tables if needed*[/COLOR]
[COLOR=#669933]*# the first time they are touched*[/COLOR]
myisam-recover         = BACKUP
[COLOR=#669933]*#max_connections        = 100*[/COLOR]
[COLOR=#669933]*#table_cache            = 64*[/COLOR]
[COLOR=#669933]*#thread_concurrency     = 10*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# * Query Cache Configuration*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
query_cache_limit    = 100M
query_cache_size        = 256M
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# * Logging and Replication*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# Both location gets rotated by the cronjob.*[/COLOR]
[COLOR=#669933]*# Be aware that this log type is a performance killer.*[/COLOR]
[COLOR=#669933]*# As of 5.1 you can enable the log at runtime!*[/COLOR]
[COLOR=#669933]*#general_log_file        = /var/log/mysql/mysql.log*[/COLOR]
[COLOR=#669933]*#general_log             = 1*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# Error log - should be very few entries.*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
log_error = /var/log/mysql/error.log
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# Here you can see queries with especially long duration*[/COLOR]
[COLOR=#669933]*#log_slow_queries    = /var/log/mysql/mysql-slow.log*[/COLOR]
[COLOR=#669933]*#long_query_time = 2*[/COLOR]
[COLOR=#669933]*#log-queries-not-using-indexes*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# The following can be used as easy to replay backup logs or for replication.*[/COLOR]
[COLOR=#669933]*# note: if you are setting up a replication slave, see README.Debian about*[/COLOR]
[COLOR=#669933]*#       other settings you may need to change.*[/COLOR]
[COLOR=#669933]*#server-id        = 1*[/COLOR]
[COLOR=#669933]*#log_bin            = /var/log/mysql/mysql-bin.log*[/COLOR]
expire_logs_days    = 10
max_binlog_size         = 100M
[COLOR=#669933]*#binlog_do_db        = include_database_name*[/COLOR]
[COLOR=#669933]*#binlog_ignore_db    = include_database_name*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# * InnoDB*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.*[/COLOR]
[COLOR=#669933]*# Read the manual for more InnoDB related options. There are many!*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# * Security Features*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# Read the manual, too, if you want chroot!*[/COLOR]
[COLOR=#669933]*# chroot = /var/lib/mysql/*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# ssl-ca=/etc/mysql/cacert.pem*[/COLOR]
[COLOR=#669933]*# ssl-cert=/etc/mysql/server-cert.pem*[/COLOR]
[COLOR=#669933]*# ssl-key=/etc/mysql/server-key.pem*[/COLOR]

innodb_buffer_pool_size = 128M

[mysqldump]
quick
quote-names
max_allowed_packet    = 128M

[mysql]
[COLOR=#669933]*#no-auto-rehash    # faster start of mysql but no tab completition*[/COLOR]

[isamchk]
key_buffer        = 256M

[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# * IMPORTANT: Additional settings that can override those from this file!*[/COLOR]
[COLOR=#669933]*#   The files must end with '.cnf', otherwise they'll be ignored.*[/COLOR]
[COLOR=#669933]*#*[/COLOR] [COLOR=#000000]![/COLOR][COLOR=#000000]includedir[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]etc[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]mysql[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]conf[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]d[/COLOR][COLOR=#000000]/[/COLOR]
```
i also added the line [COLOR=#000000]innodb_buffer_pool_size[/COLOR][COLOR=#000000]=[/COLOR][COLOR=#000000]128[/COLOR][COLOR=#000000]M as it didnt exist before. I then also created a 2GB swap in hopes that would fix it. but these changes did not.

[/COLOR]Then after this i checked RAM
```


metulburr / $ free -m             total       used       free     shared    buffers     cached
Mem:           994        851        142         54         49        389
-/+ buffers/cache:        412        581
Swap:         2047          6       2041



```
and i have seen RAM before almost maxed out. researching online seems to suggest that 1GB of RAM is not enough for a forum on a server. While others say its fine but need to just optimize apache/mysql/etc.

the respawn directive is  mysql.conf, i have never changed anythign in this file from default install. 
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

modules enabled:
```

metulburr / $ apache2ctl -M
Loaded Modules:
 core_module (static)
 so_module (static)
 watchdog_module (static)
 http_module (static)
 log_config_module (static)
 logio_module (static)
 version_module (static)
 unixd_module (static)
 access_compat_module (shared)
 alias_module (shared)
 auth_basic_module (shared)
 authn_core_module (shared)
 authn_file_module (shared)
 authz_core_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgi_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 expires_module (shared)
 fcgid_module (shared)
 filter_module (shared)
 include_module (shared)
 mime_module (shared)
 mpm_prefork_module (shared)
 negotiation_module (shared)
 php5_module (shared)
 python_module (shared)
 rewrite_module (shared)
 setenvif_module (shared)
 status_module (shared)
 wsgi_module (shared)


```

---

### Post by darkod on 2016-11-19
I'm no mysql expert but I would say any reasonable DB usage would need more than 1GB. Don't forget that the OS also needs to use part of that memory. So that's pretty low...

Here is some mysql memory calculator found on google, maybe it can help you? And that's the mysql memory usage, so you have to take into account the OS too.
[http://www.mysqlcalculator.com/](http://www.mysqlcalculator.com/)

---

### Post by SeijiSensei on 2016-11-19
I don't know what you're paying now, but for comparison a [basic Linode]("https://www.linode.com/pricing") with 2GB RAM and 24 GB SSD storage is $10/month.

---

