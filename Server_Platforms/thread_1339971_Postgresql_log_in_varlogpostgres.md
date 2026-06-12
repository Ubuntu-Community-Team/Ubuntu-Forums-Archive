---
title: "Postgresql log in /var/log/postgres"
date: 2009-11-28
forum: Server Platforms
---

### Post by misterLu on 2009-11-28
Hello all,
I have been using Gentoo for a long time but recently I switched to Ubuntu so I am not quite familiar with Ubuntu yet.

I have an Ubuntu serever where I have installed postgresql and a few perl modules. 
My problem is that I can't stop getting postgres logs in /var/log/postgresql/postgresql-8.3-main.log
My postgresql.conf file is:
```

data_directory = '/home/postgres/8.3/main'              # use data in another directory
hba_file = '/etc/postgresql/8.3/main/pg_hba.conf'       # host-based authentication file
ident_file = '/etc/postgresql/8.3/main/pg_ident.conf'   # ident configuration file
external_pid_file = '/var/run/postgresql/8.3-main.pid'          # write an extra PID file
max_connections = 140                   # (change requires restart)
shared_buffers = 128MB                  # min 128kB or max_connections*16kB
maintenance_work_mem = 512MB            # min 1MB
max_fsm_pages = 1500000                 # min max_fsm_relations*16, 6 bytes each
max_fsm_relations = 2000                # min 100, ~70 bytes each
checkpoint_segments = 30                # in logfile segments, min 1, 16MB each
log_destination = 'stderr'              # Valid values are combinations of
logging_collector = off         # Enable capturing of stderr and csvlog
log_rotation_size = 1GB         # Automatic rotation of logfiles will
log_connections = on
log_line_prefix = '%m %p %u %d %r '                     # special values:
log_lock_waits = on                     # log lock waits >= deadlock_timeout
log_statement = 'ddl'                   # none, ddl, mod, all
log_temp_files = 4096                   # log temporary files equal or larger
autovacuum = on                 # Enable autovacuum subprocess?  'on'
autovacuum_max_workers = 1              # max number of autovacuum subprocesses
autovacuum_freeze_max_age = 2000000000  # maximum XID age before forced vacuum
lc_messages = 'en_US.utf8'                      # locale for system error message
lc_monetary = 'en_US.utf8'                      # locale for monetary formatting
lc_numeric = 'en_US.utf8'                       # locale for number formatting
lc_time = 'en_US.utf8'                          # locale for time formatting
deadlock_timeout = 1s

```As you can see the logging_collector is **off** but I keep getting logs in /var/log/postgresql/postgresql-8.3-main.log
```

2009-11-28 11:12:46.873 CET 12828 systemuser dbName [local] ERROR:  duplicate key ...
```My postmaster.opts is (cat /home/postgres/8.3/main/postmaster.opts):
```

/usr/lib/postgresql/8.3/bin/postgres "-D" "/home/postgres/8.3/main" "-c" "unix_socket_directory=/var/run/postgresql" "-c" "config_file=/etc/postgresql/8.3/main/postgresql.conf"

```which confirms that my postgresql.conf was loaded. (I restarted postgres after applying changes)

My question is what forces postgresql to log in  /var/log/postgresql/postgresql-8.3-main.log?

Any tip will be  appreciated

---

### Post by windependence on 2009-11-28
Note that the default postgresql.conf file does NOT contain all possible parameters. To stop the above error and others like it from being logged, you should add the log_min_error_statement parameter to your conf file, and set it to PANIC like this:

```
log_min_error_statement = PANIC    #Turn off SQL error logging

```
Below is the full documentation from the Postgresql manual:
> log_min_error_statement (string)
 Controls whether or not the SQL statement that causes an error condition will be recorded in the server log. The current SQL statement is included in the log entry for any message of the specified severity or higher. Valid values are DEBUG5,         DEBUG4, DEBUG3,         DEBUG2, DEBUG1,         INFO, NOTICE,         WARNING, ERROR,         LOG,         FATAL, and PANIC.         The default is ERROR, which means statements causing errors, log messages, fatal errors, or panics will be logged. [COLOR=Red]To effectively turn off logging of failing statements, set this parameter to PANIC[/COLOR].         Only superusers can change this setting.

Note that with the collector off, you have only turned off logging for some items. You still have logging for access and SQL errors and possibly others. Here is a link to the documentation, which is very good and easy to follow:

[http://www.postgresql.org/docs/8.3/interactive/runtime-config-logging.html](http://www.postgresql.org/docs/8.3/interactive/runtime-config-logging.html)

Don't forget to restart Postgres after making your changes.

I'm curious, why don't you want logs? They are automatically rotated, so space is never an issue, and I would think you would want to be able to see them for troubleshooting.

-Tim

---

### Post by misterLu on 2009-11-28
Hi, thanks for quick reply.
I followed Your advice, changed conf file:
```

# grep log_min_error_statement /etc/postgresql/8.3/main/postgresql.conf
#log_min_error_statement = error        # values in order of decreasing detail:
log_min_error_statement = PANIC # values in order of decreasing detail:

```
restarted server:
```

/etc/postgresql/8.3/main# /etc/init.d/postgresql-8.3 restart
 * Restarting PostgreSQL 8.3 database server                                                                           [ OK ]

```
And nothing happens:
```

 ls -l /var/log/postgresql/postgresql-8.3-main.log
-rw-r----- 1 postgres postgres **575207** 2009-11-28 14:04 /var/log/postgresql/postgresql-8.3-main.log
root@ns365811:/etc/postgresql/8.3/main# ls -l /var/log/postgresql/postgresql-8.3-main.log
-rw-r----- 1 postgres postgres **594195** 2009-11-28 14:04 /var/log/postgresql/postgresql-8.3-main.log

```
As you can see, the log keeps growing.

> 
I'm curious, why don't you want logs? They are automatically rotated, so space is never an issue, and I would think you would want to be able to see them for troubleshooting.
I spent a lot of time analysing pg logs and pretty much know what can I expect to find. Now I have havily loaded db, which lets ~100 processes to update and write into tables.
When running the system in 'production env.' I want to switch the logging off to get higher performance.
The most often error is "error on insert - duplicate key value...". I do not know other way to check if the record is already in the table than to try to insert it. I miss mysql like 'insert ignore' here.

Anyway, the log keeps groing and I can not stop it.
Is there a chance that ubuntu syslog or anything else  forces pg to log?
Thanks in advance.

---

### Post by garance on 2012-02-07
I have the same question. We don't want to increase the size of postgresql-8.3-main.log
Does anyone have an idea ?

---

### Post by SeijiSensei on 2012-02-07
Use logrotate to manage it; see "man logrotate" for details.

---

