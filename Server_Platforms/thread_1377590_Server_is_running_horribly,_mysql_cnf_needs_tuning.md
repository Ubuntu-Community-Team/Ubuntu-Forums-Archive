---
title: "Server is running horribly, mysql cnf needs tuning help!"
date: 2010-01-10
forum: Server Platforms
---

### Post by daddysmonsters on 2010-01-10
OK, so I'm running a slice with 512mb ram (768 burstable) I have a script that is heavy, it has a lot of components that make calls to sql. I've run mysqltuner.pl and this is my output.

```
-------- General Statistics --------------------------------------------------
[--] Skipped version check for MySQLTuner script
[OK] Currently running supported MySQL version 5.0.51a-3ubuntu5.4-log
[OK] Operating on 64-bit architecture

-------- Storage Engine Statistics -------------------------------------------
[--] Status: +Archive -BDB -Federated +InnoDB -ISAM -NDBCluster 
[--] Data in MyISAM tables: 1M (Tables: 164)
[--] Data in InnoDB tables: 96K (Tables: 1)
[!!] Total fragmented tables: 16

-------- Performance Metrics -------------------------------------------------
[--] Up for: 9h 28m 49s (893K q [26.168 qps], 25K conn, TX: 1B, RX: 147M)
[--] Reads / Writes: 66% / 34%
[--] Total buffers: 58.0M global + 2.6M per thread (100 max threads)
[OK] Maximum possible memory usage: 320.5M (62% of installed RAM)
[OK] Slow queries: 0% (0/893K)
[OK] Highest usage of available connections: 6% (6/100)
[OK] Key buffer size / total MyISAM indexes: 16.0M/821.0K
[OK] Key buffer hit rate: 100.0% (6M cached / 2K reads)
[OK] Query cache efficiency: 77.9% (537K cached / 690K selects)
[!!] Query cache prunes per day: 175615
[OK] Sorts requiring temporary tables: 0% (0 temp sorts / 20K sorts)
[!!] Temporary tables created on disk: 49% (14K on disk / 30K total)
[OK] Thread cache hit rate: 99% (6 created / 25K connections)
[!!] Table cache hit rate: 2% (64 open / 2K opened)
[OK] Open file limit used: 10% (108/1K)
[OK] Table locks acquired immediately: 100% (312K immediate / 312K locks)
[OK] InnoDB data size / buffer pool: 96.0K/8.0M

-------- Recommendations -----------------------------------------------------
General recommendations:
    Run OPTIMIZE TABLE to defragment tables for better performance
    MySQL started within last 24 hours - recommendations may be inaccurate
    When making adjustments, make tmp_table_size/max_heap_table_size equal
    Reduce your SELECT DISTINCT queries without LIMIT clauses
    Increase table_cache gradually to avoid file descriptor limits
Variables to adjust:
    query_cache_size (> 16M)
    tmp_table_size (> 32M)
    max_heap_table_size (> 16M)
    table_cache (> 64)

root@spitfire:/home/zeromod# 
```From what I know, the Temp tables on disk is bad at that percentage, I need some guidelines on what people think would be a good configuration tuning. This is the default right now. I can also provide top or htop information if it would help. My site has spurts where it is nearly crippled so please help me try and resolve this.
:(

Also, at any given time my ram is only touching about 150mb even with spikes. But I feel that mysql is not being given the proper allocation of ram, and the storage is not setup properly.

---

### Post by daddysmonsters on 2010-01-12
Anyone have a clue here? I've tweaked the caching of my script and it's running much better (even without memcache on my server) But the mysqltuner.pl script still points out these issues after a 24 hour uptime.

---

### Post by daddysmonsters on 2010-01-21
bump?

---

### Post by DaithiF on 2010-01-21
sorry, not directly addressing the point here, but personally I would start by looking at the sql that is being run rather than the mysql server setup.  An inefficient query is going to cause performance issues that no amount of server tuning can address.  Have you analysed the performance of the query(/ies), looked at the steps that take longest and tried some refactoring to improve performance?

---

