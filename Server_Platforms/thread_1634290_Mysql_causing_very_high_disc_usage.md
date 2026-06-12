---
title: "Mysql causing very high disc usage"
date: 2010-11-30
forum: Server Platforms
---

### Post by nooto_ on 2010-11-30
Hi,  
 
I have noticed one of the Debian servers having crazy disk usage and  mysql seems to be causing this. If i stop the mysql the high disc usage  stops.  
 
I did some script tests to help me out. And tuned some parameters  accordingly, but this does not seem to help. The scripts just ask to  improve the same parameters more and more. I believe this has something  to do with low Table cache hit rate, and innodb_buffer_pool_size. Any  help on this would be very appreciated. 
 
Test results:

--------------------------------------------------------- 
 
TEST1 (mysqltuner.pl) 
 
-------- Storage Engine Statistics ------------------------------------------- 
[--] Status: +Archive -BDB -Federated +InnoDB -ISAM -NDBCluster 
[--] Data in InnoDB tables: 12G (Tables: 66) 
[OK] Total fragmented tables: 0 
 
-------- Performance Metrics ------------------------------------------------- 
[--] Up for: 11h 46m 19s (8M q [192.450 qps], 23K conn, TX: 3B, RX: 769M) 
[--] Reads / Writes: 59% / 41% 
[--] Total buffers: 1.1G global + 2.7M per thread (100 max threads) 
[OK] Maximum possible memory usage: 1.3G (67% of installed RAM) 
[OK] Slow queries: 0% (492/8M) 
[OK] Highest usage of available connections: 49% (49/100) 
[!!] Cannot calculate MyISAM index size - re-run script as root user 
[!!] Query cache efficiency: 18.4% (764K cached / 4M selects) 
[!!] Query cache prunes per day: 95362 
[OK] Sorts requiring temporary tables: 0% (0 temp sorts / 10K sorts) 
[!!] Temporary tables created on disk: 32% (784K on disk / 2M total) 
[OK] Thread cache hit rate: 99% (88 created / 23K connections) 
[!!] Table cache hit rate: 6% (90 open / 1K opened) 
[OK] Open file limit used: 0% (2/1K) 
[OK] Table locks acquired immediately: 100% (7M immediate / 7M locks) 
[!!] InnoDB data size / buffer pool: 12.3G/1.0G 
 
-------- Recommendations ----------------------------------------------------- 
General recommendations: 
    MySQL started within last 24 hours - recommendations may be inaccurate 
    Enable the slow query log to troubleshoot bad queries 
    When making adjustments, make tmp_table_size/max_heap_table_size equal 
    Reduce your SELECT DISTINCT queries without LIMIT clauses 
    Increase table_cache gradually to avoid file descriptor limits 
Variables to adjust: 
    query_cache_limit (> 2M, or use smaller result sets) 
    query_cache_size (> 24M) 
    tmp_table_size (> 48M) 
    max_heap_table_size (> 24M) 
    table_cache (> 90) 
    innodb_buffer_pool_size (>= 12G) 
 
 
--------------------------------------------------------------------

---

