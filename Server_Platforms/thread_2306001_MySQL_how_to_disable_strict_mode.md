---
title: "MySQL how to disable strict mode?"
date: 2015-12-11
forum: Server Platforms
---

### Post by Higgins909 on 2015-12-11
Lets say I need to use MySQL for a program but really have 0 idea how to use it...
I guess I'm the latest version, on ubuntu server 14.04.03 or something like that, you you can download a iso for.
I'm following a guide to do stuff, but its for windows... it says to edit the my.ini file... but all I can find is the-
my.cnf file.  Every time I try to edit it, mysql won't restart.

I need to find something that looks like this:
```
sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES
```[COLOR=#4C5156][FONT=segoe ui]
and replace it... not sure how I got stuck in this style of text...

Thanks,
    Higgins909

edited for wrong file type.
[/FONT][/COLOR]

---

### Post by Higgins909 on 2015-12-11
Is this not a thing or something? normally within 20 views I get a answer.
I guess I should also state that the my.cnf file looks nothing like a my.ini file.
Also upon restarting mysql service, I get such errors.

```

2015-12-11 15:33:42 5534 [Note] /usr/sbin/mysqld: Normal shutdown

2015-12-11 15:33:42 5534 [Note] Giving 0 client threads a chance to die gracefully
2015-12-11 15:33:42 5534 [Note] Event Scheduler: Purging the queue. 0 events
2015-12-11 15:33:42 5534 [Note] Shutting down slave threads
2015-12-11 15:33:42 5534 [Note] Forcefully disconnecting 0 remaining clients
2015-12-11 15:33:42 5534 [Note] Binlog end
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'partition'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'BLACKHOLE'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'ARCHIVE'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'PERFORMANCE_SCHEMA'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_SYS_DATAFILES'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_SYS_TABLESPACES'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_SYS_FOREIGN_COLS'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_SYS_FOREIGN'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_SYS_FIELDS'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_SYS_COLUMNS'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_SYS_INDEXES'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_SYS_TABLESTATS'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_SYS_TABLES'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_FT_INDEX_TABLE'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_FT_INDEX_CACHE'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_FT_CONFIG'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_FT_BEING_DELETED'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_FT_DELETED'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_FT_DEFAULT_STOPWORD'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_METRICS'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_BUFFER_POOL_STATS'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_BUFFER_PAGE_LRU'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_BUFFER_PAGE'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_CMP_PER_INDEX_RESET'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_CMP_PER_INDEX'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_CMPMEM_RESET'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_CMPMEM'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_CMP_RESET'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_CMP'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_LOCK_WAITS'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_LOCKS'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'INNODB_TRX'
2015-12-11 15:33:42 5534 [Note] Shutting down plugin 'InnoDB'
2015-12-11 15:33:42 5534 [Note] InnoDB: FTS optimize thread exiting.
2015-12-11 15:33:42 5534 [Note] InnoDB: Starting shutdown...
2015-12-11 15:33:43 5534 [Note] InnoDB: Shutdown completed; log sequence number 2954224
2015-12-11 15:33:43 5534 [Note] Shutting down plugin 'CSV'
2015-12-11 15:33:43 5534 [Note] Shutting down plugin 'MEMORY'
2015-12-11 15:33:43 5534 [Note] Shutting down plugin 'MRG_MYISAM'
2015-12-11 15:33:43 5534 [Note] Shutting down plugin 'MyISAM'
2015-12-11 15:33:43 5534 [Note] Shutting down plugin 'sha256_password'
2015-12-11 15:33:43 5534 [Note] Shutting down plugin 'mysql_old_password'
2015-12-11 15:33:43 5534 [Note] Shutting down plugin 'mysql_native_password'
2015-12-11 15:33:43 5534 [Note] Shutting down plugin 'binlog'
2015-12-11 15:33:43 5534 [Note] /usr/sbin/mysqld: Shutdown complete

151211 15:33:43 mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended
151211 15:33:43 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
2015-12-11 15:33:43 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
2015-12-11 15:33:43 0 [Note] /usr/sbin/mysqld (mysqld 5.6.27-0ubuntu0.15.04.1) starting as process 6874 ...
2015-12-11 15:33:43 6874 [Warning] Buffered warning: Changed limits: max_open_files: 1024 (requested 5000)

2015-12-11 15:33:43 6874 [Warning] Buffered warning: Changed limits: table_open_cache: 431 (requested 2000)

2015-12-11 15:33:43 6874 [Warning] Using unique option prefix myisam-recover instead of myisam-recover-options is deprecated and will be removed in a future release. Please use the full name instead.
2015-12-11 15:33:43 6874 [Note] Plugin 'FEDERATED' is disabled.
2015-12-11 15:33:43 6874 [ERROR] Function 'innodb' already exists
2015-12-11 15:33:43 6874 [Warning] Couldn't load plugin named 'innodb' with soname 'ha_innodb.so'.
2015-12-11 15:33:43 6874 [ERROR] Function 'federated' already exists
2015-12-11 15:33:43 6874 [Warning] Couldn't load plugin named 'federated' with soname 'ha_federated.so'.
2015-12-11 15:33:43 6874 [ERROR] Function 'blackhole' already exists
2015-12-11 15:33:43 6874 [Warning] Couldn't load plugin named 'blackhole' with soname 'ha_blackhole.so'.
2015-12-11 15:33:43 6874 [ERROR] Function 'archive' already exists
2015-12-11 15:33:43 6874 [Warning] Couldn't load plugin named 'archive' with soname 'ha_archive.so'.
2015-12-11 15:33:43 6874 [Note] InnoDB: Using atomics to ref count buffer pool pages
2015-12-11 15:33:43 6874 [Note] InnoDB: The InnoDB memory heap is disabled
2015-12-11 15:33:43 6874 [Note] InnoDB: Mutexes and rw_locks use GCC atomic builtins
2015-12-11 15:33:43 6874 [Note] InnoDB: Memory barrier is not used
2015-12-11 15:33:43 6874 [Note] InnoDB: Compressed tables use zlib 1.2.8
2015-12-11 15:33:43 6874 [Note] InnoDB: Using Linux native AIO
2015-12-11 15:33:43 6874 [Note] InnoDB: Not using CPU crc32 instructions
2015-12-11 15:33:43 6874 [Note] InnoDB: Initializing buffer pool, size = 128.0M
2015-12-11 15:33:43 6874 [Note] InnoDB: Completed initialization of buffer pool
2015-12-11 15:33:43 6874 [Note] InnoDB: Highest supported file format is Barracuda.
2015-12-11 15:33:43 6874 [Note] InnoDB: 128 rollback segment(s) are active.
2015-12-11 15:33:43 6874 [Note] InnoDB: Waiting for purge to start
2015-12-11 15:33:43 6874 [Note] InnoDB: 5.6.27 started; log sequence number 2954224
2015-12-11 15:33:43 6874 [Note] Server hostname (bind-address): '127.0.0.1'; port: 3306
2015-12-11 15:33:43 6874 [Note]   - '127.0.0.1' resolves to '127.0.0.1';
2015-12-11 15:33:43 6874 [Note] Server socket created on IP: '127.0.0.1'.
2015-12-11 15:33:43 6874 [Note] Event Scheduler: Loaded 0 events
2015-12-11 15:33:43 6874 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.6.27-0ubuntu0.15.04.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)

```
It's a fresh install with everything I tried to do to the my.cnf file reversed.  But I have made one schema... is that why?
What are these plugins?

---

### Post by Higgins909 on 2015-12-11
From my findings, the plugins errors are nothing to worry about and just ignore them.
Got my game server up without disabling the strict mode.

---

