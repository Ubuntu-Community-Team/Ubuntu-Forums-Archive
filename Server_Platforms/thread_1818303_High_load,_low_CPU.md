---
title: "High load, low CPU?"
date: 2011-08-04
forum: Server Platforms
---

### Post by ivotedforkodos on 2011-08-04
Can someone explain why our load is so high, but our CPU usage is so low? If there is a high load, then why aren't the CPUs working hard to finish the jobs? 

This machine has 4 CPUs and is a dedicated MySQL server. Is it reasonable to see loads this high when a few users are running a few REPLACE and UPDATE queries? I suspect that the machine is less responsive than it could be, due to a misconfiguration, but I'm not sure how to fix it.

---

### Post by psusi on 2011-08-04
Because the jobs are waiting for IO.

---

### Post by ivotedforkodos on 2011-08-04
OK, thanks. So if I/O is the bottleneck, then the only thing I can do is increase the buffer sizes that MySQL has to work with, right? They are already pretty big, but in the screenshot, memory usage is still pretty low. 

Here is my.cnf:

```

innodb_file_per_table
lower_case_table_names = 1
character-set-server = utf8
max_connections = 1000
key_buffer_size = 512M
tmp_table_size = 256M
join_buffer_size = 8M
myisam_sort_buffer_size = 256M
read_buffer_size = 2M
read_rnd_buffer_size = 8M
table_open_cache = 256
myisam_use_mmap
group_concat_max_len = 8192
# skip-name-resolve
slow-query-log

```

This machine has 8 GB of physical RAM. Should I increase the size of the buffers?

---

### Post by psusi on 2011-08-04
I'm not familiar with whatever program you got that screen shot from, so I'm not sure if its memory load counts the cache or not.  Check the output of free -m to compare.  If you have mysql using mmap, then the kernel should be using all free memory to cache the db already.

---

### Post by ivotedforkodos on 2011-08-04
> **psusi said:**
> I'm not familiar with whatever program you got that screen shot from, so I'm not sure if its memory load counts the cache or not.  Check the output of free -m to compare.  If you have mysql using mmap, then the kernel should be using all free memory to cache the db already.

That was htop
```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          7937       2674       5262          0          8       1614
-/+ buffers/cache:       1052       6884
Swap:        11293         12      11281

```

Some of the tables that we have are big (millions of rows, GBs of data), but they are partitioned. Is there any way to speed up I/O?

---

### Post by doas777 on 2011-08-04
IO is almost always a bottleneck. you can monitor your IO activity per process with iotop (run it with sudo). 
Tweaking your buffers may help, but that depends on the kinds of queries you are performing. I don't use mysql, but if you have a script/procedure, feel free to post it and we can determine if it is suboptimal.

Edit, your htop output doesn't really show no cpu. looks to me like its using 55% of each core just on those two mysqld procs. run htop with sudo and see if your graphs (at the top) don't start to match up with the top line items then.

---

### Post by Vegan on 2011-08-04
Disk performance is what is holding your rig back.

Bigger disks are faster, but only to a point.

---

### Post by ian dobson on 2011-08-05
Hi,

Increase your buffers, if this is dedicated mysql box give mysql all the ram you can spare.

Also maybe install mysqltuner ([http://mysqltuner.com/](http://mysqltuner.com/)) and see where mysql is having problems. The script doesn't change anything, it'll just report various statistics. Here's a dump from my backend sql server:-

```
 
>>  MySQLTuner 1.1.1 - Major Hayden <major@mhtx.net>
 >>  Bug reports, feature requests, and downloads at http://mysqltuner.com/
 >>  Run with '--help' for additional options and output filtering

-------- General Statistics --------------------------------------------------
[--] Skipped version check for MySQLTuner script
[OK] Currently running supported MySQL version 5.1.54-1ubuntu4
[OK] Operating on 64-bit architecture

-------- Storage Engine Statistics -------------------------------------------
[--] Status: -Archive -BDB -Federated -InnoDB -ISAM -NDBCluster
[--] Data in MyISAM tables: 360M (Tables: 228)
[!!] Total fragmented tables: 8

-------- Security Recommendations  -------------------------------------------
[OK] All database users have passwords assigned

-------- Performance Metrics -------------------------------------------------
[--] Up for: 6d 15h 18m 31s (8M q [15.264 qps], 102K conn, TX: 12B, RX: 3B)
[--] Reads / Writes: 23% / 77%
[--] Total buffers: 560.0M global + 50.6M per thread (30 max threads)
[OK] Maximum possible memory usage: 2.0G (12% of installed RAM)
[OK] Slow queries: 0% (19/8M)
[OK] Highest usage of available connections: 56% (17/30)
[OK] Key buffer size / total MyISAM indexes: 400.0M/334.6M
[OK] Key buffer hit rate: 99.0% (173M cached / 1M reads)
[OK] Query cache efficiency: 80.7% (4M cached / 4M selects)
[OK] Query cache prunes per day: 0
[OK] Sorts requiring temporary tables: 0% (90 temp sorts / 307K sorts)
[!!] Joins performed without indexes: 2848
[OK] Temporary tables created on disk: 2% (5K on disk / 222K total)
[OK] Thread cache hit rate: 99% (17 created / 102K connections)
[!!] Table cache hit rate: 1% (501 open / 31K opened)
[OK] Open file limit used: 9% (752/8K)
[OK] Table locks acquired immediately: 99% (4M immediate / 4M locks)

-------- Recommendations -----------------------------------------------------
General recommendations:
    Run OPTIMIZE TABLE to defragment tables for better performance
    Enable the slow query log to troubleshoot bad queries
    Adjust your join queries to always utilize indexes
    Increase table_cache gradually to avoid file descriptor limits
Variables to adjust:
    join_buffer_size (> 48.0M, or always use indexes with joins)
    table_cache (> 4096)

```

Regards
Ian Dobson

---

### Post by psusi on 2011-08-06
Sounds like you may need to create some indexes to reduce how much IO needs done to satisfy the queries.

---

