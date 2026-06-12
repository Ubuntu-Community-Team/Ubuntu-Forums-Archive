---
title: "where is the mysql error log"
date: 2010-08-29
forum: Server Platforms
---

### Post by jrtboht on 2010-08-29
I can't seem to find where mysql error logs are kept.  I've generated a few errors and then checked /var/log/syslog, /var/log/mysql.log and /var/log/mysql/error.log and didn't see mysql errors in any of those files.  The 2 mysql files were empty and I didn't see any mysql errors in syslog.

Here is the what the logging portion of my.cnf looks like.

```
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
# As of 5.1 you can enable the log at runtime!
#general_log_file        = /var/log/mysql/mysql.log
#general_log             = 1

log_error                = /var/log/mysql/error.log

# Here you can see queries with especially long duration
#log_slow_queries       = /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id              = 1
#log_bin                        = /var/log/mysql/mysql-bin.log
expire_logs_days        = 10
max_binlog_size         = 100M
#binlog_do_db           = include_database_name
#binlog_ignore_db       = include_database_name
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem
```

---

### Post by maikel.b on 2010-08-29
oke maybe this is the one you need....

 cat /var/log/mysql.err

greetz maikel.b

---

### Post by jrtboht on 2010-08-29
There is nothing in /var/log/mysql.err either

---

