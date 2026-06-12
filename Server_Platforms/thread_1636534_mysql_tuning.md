---
title: "mysql tuning"
date: 2010-12-03
forum: Server Platforms
---

### Post by MuschPusch on 2010-12-03
Hey, 

i'm running the tuning_primer.sh for tuning mysql and i don't really understand the output: 


TABLE CACHE
Current table_open_cache = 1500 tables
Current table_definition_cache = 1812 tables
You have a total of 1425 tables
You have 1500 open tables.
Current table_cache hit rate is 13%
, while 100% of your table cache is in use
You should probably increase your table_cache

I have a total of 1425 tables... But how can i have 1500 open tables? An a table_cache hit rate of only 13%?????

Someone an idea?

regards Volkan

---

### Post by DaithiF on 2010-12-03
> **MuschPusch said:**
> 
I have a total of 1425 tables... But how can i have 1500 open tables? 

if you have 2 simultaneous connections, each querying the same table, mysql opens that table twice.  So its common to have more open tables than actual tables.

> **MuschPusch said:**
> 
An a table_cache hit rate of only 13%?????

When mysql opens a table it stores the opened file descriptor for that table in a cache, so that when the next query comes along that accesses that table, it can use the already-opened file descriptor (as long as the first query has completed).

The table_open_cache setting sets a limit for the number of table file descriptors that get cached.  In your case its 1500.  The cache hit rate describes the % of times a table file-descriptor was available to use in the cache (as opposed to having to open the table again).  A cache size of 1500 is probably low when you have 1425 tables, though it really depends on how many of those tables are being frequently accessed, and by how many concurrent connections.  You could increase the table_open_cache but be aware that at the OS level you need the mysqld process to be able to open that number of simultaneous file descriptors -- the usual starting limit on linux is actually 1024 per process, and you're already more that that (run ulimit -n to see the current value).

---

