---
title: "Mysql CPU Usage 170%"
date: 2017-07-11
forum: Server Platforms
---

### Post by monster-it on 2017-07-11
Hi,

Hope someone can help me. I have a VPS on a DL380 g5 the vps has 3 cores with 6gb ram and 120gb hdd. However the mysql keeps going up to 170% and more. i restart the service it's fine for 15 - 20 mins then boom the server nearly grinds to a hault.
Here is my mysqltuner output.
```
[OK] Operating on 64-bit architecture

-------- Log file Recommendations ------------------------------------------------------------------
[--] Log file: /var/log/mysql/error.log(217K)
[OK] Log file /var/log/mysql/error.log exists
[OK] Log file /var/log/mysql/error.log is readable.
[OK] Log file /var/log/mysql/error.log is not empty
[OK] Log file /var/log/mysql/error.log is smaller than 32 Mb
[!!] /var/log/mysql/error.log contains 68 warning(s).
[!!] /var/log/mysql/error.log contains 115 error(s).
[--] 15 start(s) detected in /var/log/mysql/error.log
[--] 1) 2017-07-11T17:31:19.137881Z 0 [Note] /usr/sbin/mysqld: ready for connections.
[--] 2) 2017-07-11T17:31:04.157604Z 0 [Note] /usr/sbin/mysqld: ready for connections.
[--] 3) 2017-07-11T17:30:44.392633Z 0 [Note] /usr/sbin/mysqld: ready for connections.
[--] 4) 2017-07-11T17:27:33.946023Z 0 [Note] /usr/sbin/mysqld: ready for connections.
[--] 5) 2017-07-11T17:26:53.968865Z 0 [Note] /usr/sbin/mysqld: ready for connections.
[--] 6) 2017-07-11T17:22:43.646019Z 0 [Note] /usr/sbin/mysqld: ready for connections.
[--] 7) 2017-07-11T17:21:53.988417Z 0 [Note] /usr/sbin/mysqld: ready for connections.
[--] 8) 2017-07-11T17:09:30.748352Z 0 [Note] /usr/sbin/mysqld: ready for connections.
[--] 9) 2017-07-11T12:16:36.234917Z 0 [Note] /usr/sbin/mysqld: ready for connections.
[--] 10) 2017-07-11T10:29:28.147523Z 0 [Note] /usr/sbin/mysqld: ready for connections.
[--] 13 shutdown(s) detected in /var/log/mysql/error.log
[--] 1) 2017-07-11T17:31:18.251678Z 0 [Note] /usr/sbin/mysqld: Shutdown complete
[--] 2) 2017-07-11T17:31:03.263566Z 0 [Note] /usr/sbin/mysqld: Shutdown complete
[--] 3) 2017-07-11T17:30:43.366214Z 0 [Note] /usr/sbin/mysqld: Shutdown complete
[--] 4) 2017-07-11T17:27:33.140074Z 0 [Note] /usr/sbin/mysqld: Shutdown complete
[--] 5) 2017-07-11T17:26:53.131944Z 0 [Note] /usr/sbin/mysqld: Shutdown complete
[--] 6) 2017-07-11T17:22:42.941694Z 0 [Note] /usr/sbin/mysqld: Shutdown complete
[--] 7) 2017-07-11T17:21:52.995197Z 0 [Note] /usr/sbin/mysqld: Shutdown complete
[--] 8) 2017-07-11T17:05:31.490360Z 0 [Note] /usr/sbin/mysqld: Shutdown complete
[--] 9) 2017-07-11T12:12:35.976532Z 0 [Note] /usr/sbin/mysqld: Shutdown complete
[--] 10) 2017-07-11T10:25:24.201706Z 0 [Note] /usr/sbin/mysqld: Shutdown complete


-------- Storage Engine Statistics -----------------------------------------------------------------
[--] Status: +ARCHIVE +BLACKHOLE +CSV -FEDERATED +InnoDB +MEMORY +MRG_MYISAM +MyISAM +PERFORMANCE_SCHEMA
[--] Data in InnoDB tables: 429M (Tables: 53)
[--] Data in MyISAM tables: 140M (Tables: 40)
[OK] Total fragmented tables: 0


-------- Security Recommendations ------------------------------------------------------------------
[OK] There are no anonymous accounts for any database users
[OK] All database users have passwords assigned
[--] There are 605 basic passwords in the list.


-------- CVE Security Recommendations --------------------------------------------------------------
[--] Skipped due to --cvefile option undefined


-------- Performance Metrics -----------------------------------------------------------------------
[--] Up for: 26m 32s (339K q [213.303 qps], 3K conn, TX: 2G, RX: 40M)
[--] Reads / Writes: 97% / 3%
[--] Binary logging is disabled
[--] Physical Memory     : 5.8G
[--] Max MySQL memory    : 1.2G
[--] Other process memory: 2.1G
[--] Total buffers: 1.1G global + 1.1M per thread (151 max threads)
[--] P_S Max memory usage: 72B
[--] Galera GCache Max memory usage: 0B
[OK] Maximum reached memory usage: 1.1G (18.77% of installed RAM)
[OK] Maximum possible memory usage: 1.2G (20.95% of installed RAM)
[OK] Overall possible memory usage with other process is compatible with memory available
[OK] Slow queries: 0% (0/339K)
[OK] Highest usage of available connections: 19% (29/151)
[OK] Aborted connections: 0.22%  (7/3208)
[!!] name resolution is active : a reverse name resolution is made for each new connection and can reduce performance
[!!] Query cache may be disabled by default due to mutex contention.
[!!] Query cache efficiency: 0.0% (0 cached / 305K selects)
[OK] Query cache prunes per day: 0
[OK] Sorts requiring temporary tables: 0% (547 temp sorts / 61K sorts)
[!!] Joins performed without indexes: 2156
[!!] Temporary tables created on disk: 61% (19K on disk / 31K total)
[OK] Thread cache hit rate: 97% (92 created / 3K connections)
[!!] Table cache hit rate: 12% (416 open / 3K opened)
[OK] Open file limit used: 31% (324/1K)
[!!] Table locks acquired immediately: 93%


-------- Performance schema ------------------------------------------------------------------------
[--] Memory used by P_S: 72B
[--] Sys schema is installed.


-------- ThreadPool Metrics ------------------------------------------------------------------------
[--] ThreadPool stat is disabled.


-------- MyISAM Metrics ----------------------------------------------------------------------------
[OK] Key buffer used: 96.4% (16M used / 16M cache)
[OK] Key buffer size / total MyISAM indexes: 16.0M/37.4M
[OK] Read Key buffer hit rate: 99.9% (14M cached / 13K reads)
[!!] Write Key buffer hit rate: 89.1% (2K cached / 2K writes)


-------- InnoDB Metrics ----------------------------------------------------------------------------
[--] InnoDB is enabled.
[--] InnoDB Thread Concurrency: 0
[OK] InnoDB File per table is activated
[OK] InnoDB buffer pool / data size: 1.0G/429.4M
[!!] Ratio InnoDB log file size / InnoDB Buffer pool size (9.375 %): 48.0M * 2/1.0G should be equal 25%
[!!] InnoDB buffer pool <= 1G and Innodb_buffer_pool_instances(!=1).
[--] Number of InnoDB Buffer Pool Chunk : 8 for 8 Buffer Pool Instance(s)
[OK] Innodb_buffer_pool_size aligned with Innodb_buffer_pool_chunk_size & Innodb_buffer_pool_instances
[OK] InnoDB Read buffer efficiency: 99.97% (2982188 hits/ 2983025 total)
[!!] InnoDB Write Log efficiency: 61.94% (166 hits/ 268 total)
[OK] InnoDB log waits: 0.00% (0 waits / 102 writes)


-------- AriaDB Metrics ----------------------------------------------------------------------------
[--] AriaDB is disabled.


-------- TokuDB Metrics ----------------------------------------------------------------------------
[--] TokuDB is disabled.


-------- XtraDB Metrics ----------------------------------------------------------------------------
[--] XtraDB is disabled.


-------- RocksDB Metrics ---------------------------------------------------------------------------
[--] RocksDB is disabled.


-------- Spider Metrics ----------------------------------------------------------------------------
[--] Spider is disabled.


-------- Connect Metrics ---------------------------------------------------------------------------
[--] Connect is disabled.


-------- Galera Metrics ----------------------------------------------------------------------------
[--] Galera is disabled.


-------- Replication Metrics -----------------------------------------------------------------------
[--] Galera Synchronous replication: NO
[--] No replication slave(s) for this server.
[--] This is a standalone server.


-------- Recommendations ---------------------------------------------------------------------------
General recommendations:
    Control warning line(s) into /var/log/mysql/error.log file
    Control error line(s) into /var/log/mysql/error.log file
    MySQL started within last 24 hours - recommendations may be inaccurate
    Configure your accounts with ip or subnets only, then update your configuration with skip-name-resolve=1
    Adjust your join queries to always utilize indexes
    When making adjustments, make tmp_table_size/max_heap_table_size equal
    Reduce your SELECT DISTINCT queries which have no LIMIT clause
    Increase table_open_cache gradually to avoid file descriptor limits
    Read this before increasing table_open_cache over 64: http://bit.ly/1mi7c4C
    Beware that open_files_limit (1024) variable
    should be greater than table_open_cache (431)
    Optimize queries and/or use InnoDB to reduce lock wait
Variables to adjust:
    query_cache_size (=0)
    query_cache_type (=0)
    query_cache_limit (> 1M, or use smaller result sets)
    join_buffer_size (> 256.0K, or always use indexes with joins)
    tmp_table_size (> 16M)
    max_heap_table_size (> 16M)
    table_open_cache (> 431)
    innodb_log_file_size * innodb_log_files_in_group should be equal to 1/4 of buffer pool size (=512M) if possible.
    innodb_buffer_pool_instances (=1)

```

now my vmstat 3 output.
```
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 3  0      0 4024296  68528 996072    0    0    92    29  155  490 38 20 41  1  0
 4  0      0 4004580  68544 996108    0    0    33    21  610 1694 39 20 40  0  0
 1  0      0 3940632  68544 996188    0    0     0     0  390 1511 48 25 27  0  0
 2  0      0 3959644  68552 996196    0    0     0    35  416 1573 42 15 43  0  0
 2  0      0 3999848  68560 996380    0    0    84    15  442 1215 32 14 54  1  0
 1  0      0 4009988  68560 995944    0    0     0     0  340 1099 33 18 49  0  0
 1  0      0 4011532  68568 995860    0    0     0    45  459 1553 43 22 35  0  0

```

my df -h output

```
Filesystem      Size  Used Avail Use% Mounted on
udev            2.9G     0  2.9G   0% /dev
tmpfs           596M   16M  581M   3% /run
/dev/sda1        93G   25G   64G  28% /
tmpfs           3.0G     0  3.0G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           3.0G     0  3.0G   0% /sys/fs/cgroup
tmpfs           596M     0  596M   0% /run/user/1000

```

my top command.
```
 top - 19:02:31 up 56 min,  2 users,  load average: 3.73, 3.05, 2.97Tasks: 153 total,   3 running, 150 sleeping,   0 stopped,   0 zombie
%Cpu(s): 38.8 us, 21.0 sy,  0.0 ni, 40.1 id,  0.0 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem :  6102204 total,  3770324 free,  1258796 used,  1073084 buff/cache
KiB Swap:  6288380 total,  6288380 free,        0 used.  4496716 avail Mem


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 3480 mysql     20   0 3129000 514260  19104 S 134.9  8.4  36:59.67 mysqld
10095 www-data  20   0  507780  85876  53520 S   7.3  1.4   0:00.35 apache2
10073 www-data  20   0  426900  73596  46204 S   6.3  1.2   0:00.44 apache2
10093 www-data  20   0  507240  85220  53396 S   5.3  1.4   0:00.30 apache2
10069 www-data  20   0  508928  89828  56408 S   4.0  1.5   0:00.66 apache2
10062 www-data  20   0  498780  80568  57080 S   3.0  1.3   0:00.88 apache2
10015 www-data  20   0  505504  87500  57336 S   2.7  1.4   0:02.22 apache2
10018 www-data  20   0  511408  94528  58356 S   2.7  1.5   0:04.46 apache2
10039 www-data  20   0  519284 105648  61656 S   2.7  1.7   0:01.99 apache2
10020 www-data  20   0  511176  94116  58136 S   2.0  1.5   0:04.31 apache2
10066 www-data  20   0  513184  95616  57660 S   2.0  1.6   0:01.79 apache2
10094 www-data  20   0  412244  38880  26460 R   1.7  0.6   0:00.10 apache2
 8179 www-data  20   0  511600  98320  61976 S   1.3  1.6   0:07.60 apache2
10044 www-data  20   0  509232  95128  61116 S   0.7  1.6   0:03.06 apache2
10045 www-data  20   0  509132  91148  57232 S   0.7  1.5   0:02.32 apache2
10068 www-data  20   0  496404  77208  56228 S   0.7  1.3   0:00.56 apache2
    7 root      20   0       0      0      0 R   0.3  0.0   0:10.49 rcu_sched
 2071 monster+  20   0   41996   4004   3240 S   0.3  0.1   0:08.69 top
 2617 root      20   0  407032  33436  25944 S   0.3  0.5   0:04.70 apache2
 7988 root      20   0       0      0      0 S   0.3  0.0   0:00.80 kworker/0:1
10048 www-data  20   0  499128  85808  62000 S   0.3  1.4   0:01.58 apache2
    1 root      20   0   37608   5676   4004 S   0.0  0.1   0:03.90 systemd
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd

```





any help would be greatly appreciated as I have no idea what's causing it.

---

### Post by SeijiSensei on 2017-07-11
One problem might be related to this:

> [!!] Joins performed without indexes: 2156

Do you have indexes on all your tables?  In particular, any foreign keys need to be indexed on the joined fields, and, of course, the referenced foreign key needs to be indexed as well.  Examine all the queries in your application, and make sure any referenced fields (joins, WHERE clauses, etc.) are indexed.  If you query on multiple fields, create indexes that include all those fields as well.

Lack of good indexing is a primary reason for poor query performance as the DB engine must scan the actual records for the matching fields or values.

---

