---
title: "MySQL and Jinzora"
date: 2009-02-07
forum: Server Platforms
---

### Post by Solaris3k1 on 2009-02-07
Hi, I'm trying to set up Jinzora on a server I've set up within my LAN for outside access to my media.

Problem is, I'm not sure that my MySQL server is accessible as it keeps on spitting back 

"Creating Database
    - jinzora2 - Failed!

could not connect to database."

When it sets up the backend (which is the MySQL database)

I'd post over at their forums, but they don't seem to respond to this issue in any of the threads I looked at and I've been trying to figure this out for almost 2 days.  Any help would be appreciated.

I'm going to bed relatively soon, and it is an ungodly hour, but if anyone needs to see an output of anything, I'll provide it ASAP.

---

### Post by volkswagner on 2009-02-07
Jinzora needs mysql root access to create the database.  

First verify you can access mysql as root user with password.

```
mysql -u root -p
```

---

### Post by Solaris3k1 on 2009-02-07
I can connect to mysql as both root and as a user given root access through phpmyadmin and through the terminal.

```
root@armory:/var/www/jinzora2/temp# mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 10
Server version: 5.0.51a-3ubuntu5.4 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 

```

or

```
root@armory:/var/www/jinzora2/temp# mysql -u epea -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 11
Server version: 5.0.51a-3ubuntu5.4 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 

```

I've also tried entering both root and epea as my username during the jinzora2 setup and properly entered the passwords.

I also tried to manually create the database through phpmyadmin as well as through the MySQL prompt in terminal, but that didn't seem to do anything either.

---

### Post by Solaris3k1 on 2009-02-08
Here's an update/a little more information from my phpmyadmin page.

MySQL Status


Server: localhost

    * DatabasesDatabases
    * SQLSQL
    * StatusStatus
    * VariablesVariables
    * CharsetsCharsets
    * EnginesEngines
    * PrivilegesPrivileges
    * ProcessesProcesses
    * ExportExport
    * ImportImport


Runtime Information
Refresh Reset Documentation

This MySQL server has been running for 1 days, 9 hours, 50 minutes and 25 seconds. It started up on Feb 07, 2009 at 03:41 AM.
SQL query InnoDB NDB SSL Handler Query cache Threads Binary log Temporary data Delayed inserts Key cache Joins Replication Sorting Tables Transaction coordinator
Server traffic: These tables show the network traffic statistics of this MySQL server since its startup.
Traffic Tip 	ø per hour
Received 	7,617 B 	225 B
Sent 	113 KiB 	3,424 B
Total 	121 KiB 	3,649 B
Connections 	ø per hour 	%
max. concurrent connections 	1 	--- 	---
Failed attempts 	3 	0.00 k 	13.04%
Aborted 	0 	0.00 	0.00%
Total 	23 	0.00 k 	100.00%
Query statistics: Since its startup, 205 queries have been sent to the server.
Total 	ø per hour 	ø per minute 	ø per second
205 	6.06 	0.00 k 	0.00 k
Query type 	ø per hour 	%
admin commands 	3 	0.00 k 	1.65%
alter db 	0 	0.00 	0.00%
alter table 	0 	0.00 	0.00%
analyze 	0 	0.00 	0.00%
backup table 	0 	0.00 	0.00%
begin 	0 	0.00 	0.00%
call procedure 	0 	0.00 	0.00%
change db 	8 	0.00 k 	4.40%
change master 	0 	0.00 	0.00%
check 	27 	0.00 k 	14.84%
checksum 	0 	0.00 	0.00%
commit 	0 	0.00 	0.00%
create db 	0 	0.00 	0.00%
create function 	0 	0.00 	0.00%
create index 	0 	0.00 	0.00%
create table 	0 	0.00 	0.00%
create user 	0 	0.00 	0.00%
delete 	0 	0.00 	0.00%
delete multi 	0 	0.00 	0.00%
do 	0 	0.00 	0.00%
drop db 	0 	0.00 	0.00%
drop function 	0 	0.00 	0.00%
drop index 	0 	0.00 	0.00%
drop table 	0 	0.00 	0.00%
drop user 	0 	0.00 	0.00%
flush 	1 	0.00 k 	0.55%
grant 	0 	0.00 	0.00%
ha close 	0 	0.00 	0.00%
ha open 	0 	0.00 	0.00%
ha read 	0 	0.00 	0.00%
help 	0 	0.00 	0.00%
insert 	0 	0.00 	0.00%
insert select 	0 	0.00 	0.00%
kill 	0 	0.00 	0.00%
load 	0 	0.00 	0.00%
load master data 	0 	0.00 	0.00%
load master table 	0 	0.00 	0.00%
lock tables 	0 	0.00 	0.00%
optimize 	0 	0.00 	0.00%
preload keys 	0 	0.00 	0.00%
purge 	0 	0.00 	0.00%
purge before date 	0 	0.00 	0.00%
rename table 	0 	0.00 	0.00%
repair 	0 	0.00 	0.00%
replace 	0 	0.00 	0.00%
replace select 	0 	0.00 	0.00%
reset 	0 	0.00 	0.00%
restore table 	0 	0.00 	0.00%
revoke 	0 	0.00 	0.00%
revoke all 	0 	0.00 	0.00%
Query type 	ø per hour 	%
rollback 	0 	0.00 	0.00%
savepoint 	0 	0.00 	0.00%
select 	29 	0.00 k 	15.93%
set option 	36 	1.06 	19.78%
show binlog events 	0 	0.00 	0.00%
show binlogs 	5 	0.00 k 	2.75%
show charsets 	9 	0.00 k 	4.95%
show collations 	9 	0.00 k 	4.95%
show column types 	0 	0.00 	0.00%
show create db 	0 	0.00 	0.00%
show create table 	0 	0.00 	0.00%
show databases 	10 	0.00 k 	5.49%
show errors 	0 	0.00 	0.00%
show fields 	0 	0.00 	0.00%
show grants 	2 	0.00 k 	1.10%
show innodb status 	0 	0.00 	0.00%
show keys 	0 	0.00 	0.00%
show logs 	0 	0.00 	0.00%
show master status 	0 	0.00 	0.00%
show ndb status 	0 	0.00 	0.00%
show new master 	0 	0.00 	0.00%
show open tables 	0 	0.00 	0.00%
show privileges 	0 	0.00 	0.00%
show processlist 	0 	0.00 	0.00%
show slave hosts 	0 	0.00 	0.00%
show slave status 	0 	0.00 	0.00%
show status 	2 	0.00 k 	1.10%
show storage engines 	0 	0.00 	0.00%
show tables 	17 	0.00 k 	9.34%
show triggers 	0 	0.00 	0.00%
show variables 	32 	0.00 k 	17.58%
show warnings 	0 	0.00 	0.00%
slave start 	0 	0.00 	0.00%
slave stop 	0 	0.00 	0.00%
stmt close 	0 	0.00 	0.00%
stmt execute 	0 	0.00 	0.00%
stmt fetch 	0 	0.00 	0.00%
stmt prepare 	0 	0.00 	0.00%
stmt reset 	0 	0.00 	0.00%
stmt send long data 	0 	0.00 	0.00%
truncate 	0 	0.00 	0.00%
unlock tables 	0 	0.00 	0.00%
update 	0 	0.00 	0.00%
update multi 	0 	0.00 	0.00%
xa commit 	0 	0.00 	0.00%
xa end 	0 	0.00 	0.00%
xa prepare 	0 	0.00 	0.00%
xa recover 	0 	0.00 	0.00%
xa rollback 	0 	0.00 	0.00%
xa start 	0 	0.00 	0.00%
Begin SQL query Variable 	Value 	Description
Flush_commands 	1 	The number of executed FLUSH statements.
Last_query_cost 	0 	The total cost of the last compiled query as computed by the query optimizer. Useful for comparing the cost of different query plans for the same query. The default value of 0 means that no query has been compiled yet.
Slow_queries 	0 	The number of queries that have taken more than long_query_time seconds.Documentation
Begin InnoDB Variable 	Value 	Description
Variables InnoDB Status Documentation
Innodb_buffer_pool_pages_data 	19 	The number of pages containing data (dirty or clean).
Innodb_buffer_pool_pages_dirty 	0 	The number of pages currently dirty.
Innodb_buffer_pool_pages_flushed 	0 	The number of buffer pool pages that have been requested to be flushed.
Innodb_buffer_pool_pages_free 	493 	The number of free pages.
Innodb_buffer_pool_pages_latched 	0 	The number of latched pages in InnoDB buffer pool. These are pages currently being read or written or that can't be flushed or removed for some other reason.
Innodb_buffer_pool_pages_misc 	0 	The number of pages busy because they have been allocated for administrative overhead such as row locks or the adaptive hash index. This value can also be calculated as Innodb_buffer_pool_pages_total - Innodb_buffer_pool_pages_free - Innodb_buffer_pool_pages_data.
Innodb_buffer_pool_pages_total 	512 	Total size of buffer pool, in pages.
Innodb_buffer_pool_read_ahead_rnd 	1 	The number of "random" read-aheads InnoDB initiated. This happens when a query is to scan a large portion of a table but in random order.
Innodb_buffer_pool_read_ahead_seq 	0 	The number of sequential read-aheads InnoDB initiated. This happens when InnoDB does a sequential full table scan.
Innodb_buffer_pool_read_requests 	77 	The number of logical read requests InnoDB has done.
Innodb_buffer_pool_reads 	12 	The number of logical reads that InnoDB could not satisfy from buffer pool and had to do a single-page read.
Innodb_buffer_pool_wait_free 	0 	Normally, writes to the InnoDB buffer pool happen in the background. However, if it's necessary to read or create a page and no clean pages are available, it's necessary to wait for pages to be flushed first. This counter counts instances of these waits. If the buffer pool size was set properly, this value should be small.
Innodb_buffer_pool_write_requests 	0 	The number writes done to the InnoDB buffer pool.
Innodb_data_fsyncs 	3 	The number of fsync() operations so far.
Innodb_data_pending_fsyncs 	0 	The current number of pending fsync() operations.
Innodb_data_pending_reads 	0 	The current number of pending reads.
Innodb_data_pending_writes 	0 	The current number of pending writes.
Innodb_data_read 	2,494 k 	The amount of data read so far, in bytes.
Innodb_data_reads 	25 	The total number of data reads.
Innodb_data_writes 	3 	The total number of data writes.
Innodb_data_written 	1,536 	The amount of data written so far, in bytes.
Innodb_dblwr_pages_written 	0 	The number of doublewrite writes that have been performed and the number of pages that have been written for this purpose.
Innodb_dblwr_writes 	0 	The number of doublewrite writes that have been performed and the number of pages that have been written for this purpose.
Innodb_log_waits 	0 	The number of waits we had because log buffer was too small and we had to wait for it to be flushed before continuing.
Innodb_log_write_requests 	0 	The number of log write requests.
Innodb_log_writes 	1 	The number of physical writes to the log file.
Innodb_os_log_fsyncs 	3 	The number of fsyncs writes done to the log file.
Innodb_os_log_pending_fsyncs 	0 	The number of pending log file fsyncs.
Innodb_os_log_pending_writes 	0 	Pending log file writes.
Innodb_os_log_written 	512 	The number of bytes written to the log file.
Innodb_page_size 	16 k 	The compiled-in InnoDB page size (default 16KB). Many values are counted in pages; the page size allows them to be easily converted to bytes.
Innodb_pages_created 	0 	The number of pages created.
Innodb_pages_read 	19 	The number of pages read.
Innodb_pages_written 	0 	The number of pages written.
Innodb_row_lock_current_waits 	0 	The number of row locks currently being waited for.
Innodb_row_lock_time 	0 	The total time spent in acquiring row locks, in milliseconds.
Innodb_row_lock_time_avg 	0 	The average time to acquire a row lock, in milliseconds.
Innodb_row_lock_time_max 	0 	The maximum time to acquire a row lock, in milliseconds.
Innodb_row_lock_waits 	0 	The number of times a row lock had to be waited for.
Innodb_rows_deleted 	0 	The number of rows deleted from InnoDB tables.
Innodb_rows_inserted 	0 	The number of rows inserted in InnoDB tables.
Innodb_rows_read 	0 	The number of rows read from InnoDB tables.
Innodb_rows_updated 	0 	The number of rows updated in InnoDB tables.
Begin NDB Variable 	Value 	Description
Ndb_cluster_node_id 	0 	
Ndb_config_from_host 		
Ndb_config_from_port 	0 	
Ndb_number_of_data_nodes 	0 	
Begin SSL Variable 	Value 	Description
Ssl_accept_renegotiates 	0 	
Ssl_accepts 	0 	
Ssl_callback_cache_hits 	0 	
Ssl_cipher 		
Ssl_cipher_list 		
Ssl_client_connects 	0 	
Ssl_connect_renegotiates 	0 	
Ssl_ctx_verify_depth 	0 	
Ssl_ctx_verify_mode 	0 	
Ssl_default_timeout 	0 	
Ssl_finished_accepts 	0 	
Ssl_finished_connects 	0 	
Ssl_session_cache_hits 	0 	
Ssl_session_cache_misses 	0 	
Ssl_session_cache_mode 	NONE 	
Ssl_session_cache_overflows 	0 	
Ssl_session_cache_size 	0 	
Ssl_session_cache_timeouts 	0 	
Ssl_sessions_reused 	0 	
Ssl_used_session_cache_entries 	0 	
Ssl_verify_depth 	0 	
Ssl_verify_mode 	0 	
Ssl_version 		
Begin Handler Variable 	Value 	Description
Handler_commit 	0 	The number of internal COMMIT statements.
Handler_delete 	0 	The number of times a row was deleted from a table.
Handler_discover 	0 	The MySQL server can ask the NDB Cluster storage engine if it knows about a table with a given name. This is called discovery. Handler_discover indicates the number of time tables have been discovered.
Handler_prepare 	0 	
Handler_read_first 	3 	The number of times the first entry was read from an index. If this is high, it suggests that the server is doing a lot of full index scans; for example, SELECT col1 FROM foo, assuming that col1 is indexed.
Handler_read_key 	0 	The number of requests to read a row based on a key. If this is high, it is a good indication that your queries and tables are properly indexed.
Handler_read_next 	0 	The number of requests to read the next row in key order. This is incremented if you are querying an index column with a range constraint or if you are doing an index scan.
Handler_read_prev 	0 	The number of requests to read the previous row in key order. This read method is mainly used to optimize ORDER BY ... DESC.
Handler_read_rnd 	0 	The number of requests to read a row based on a fixed position. This is high if you are doing a lot of queries that require sorting of the result. You probably have a lot of queries that require MySQL to scan whole tables or you have joins that don't use keys properly.
Handler_read_rnd_next 	2,945 	The number of requests to read the next row in the data file. This is high if you are doing a lot of table scans. Generally this suggests that your tables are not properly indexed or that your queries are not written to take advantage of the indexes you have.
Handler_rollback 	0 	The number of internal ROLLBACK statements.
Handler_savepoint 	0 	
Handler_savepoint_rollback 	0 	
Handler_update 	0 	The number of requests to update a row in a table.
Handler_write 	2,842 	The number of requests to insert a row in a table.
Begin Query cache Variable 	Value 	Description
Flush query cache Documentation
Qcache_free_blocks 	1 	The number of free memory blocks in query cache.
Qcache_free_memory 	17 M 	The amount of free memory for query cache.
Qcache_hits 	0 	The number of cache hits.
Qcache_inserts 	0 	The number of queries added to the cache.
Qcache_lowmem_prunes 	0 	The number of queries that have been removed from the cache to free up memory for caching new queries. This information can help you tune the query cache size. The query cache uses a least recently used (LRU) strategy to decide which queries to remove from the cache.
Qcache_not_cached 	108 	The number of non-cached queries (not cachable, or not cached due to the query_cache_type setting).
Qcache_queries_in_cache 	0 	The number of queries registered in the cache.
Qcache_total_blocks 	1 	The total number of blocks in the query cache.
Begin Threads Variable 	Value 	Description
Show processes Documentation
Slow_launch_threads 	0 	The number of threads that have taken more than slow_launch_time seconds to create.
Threads_cached 	0 	The number of threads in the thread cache. The cache hit rate can be calculated as Threads_created/Connections. If this value is red you should raise your thread_cache_size.
Threads_connected 	1 	The number of currently open connections.
Threads_created 	1 	The number of threads created to handle connections. If Threads_created is big, you may want to increase the thread_cache_size value. (Normally this doesn't give a notable performance improvement if you have a good thread implementation.)
Threads_running 	1 	The number of threads that are not sleeping.
Threads_cache_hitrate_% 	95.65 % 	
Begin Binary log Variable 	Value 	Description
Documentation
Binlog_cache_disk_use 	0 	The number of transactions that used the temporary binary log cache but that exceeded the value of binlog_cache_size and used a temporary file to store statements from the transaction.
Binlog_cache_use 	0 	The number of transactions that used the temporary binary log cache.
Begin Temporary data Variable 	Value 	Description
Created_tmp_disk_tables 	0 	The number of temporary tables on disk created automatically by the server while executing statements. If Created_tmp_disk_tables is big, you may want to increase the tmp_table_size value to cause temporary tables to be memory-based instead of disk-based.
Created_tmp_files 	5 	How many temporary files mysqld has created.
Created_tmp_tables 	79 	The number of in-memory temporary tables created automatically by the server while executing statements.
Begin Delayed inserts Variable 	Value 	Description
Delayed_errors 	0 	The number of rows written with INSERT DELAYED for which some error occurred (probably duplicate key).
Delayed_insert_threads 	0 	The number of INSERT DELAYED handler threads in use. Every different table on which one uses INSERT DELAYED gets its own thread.
Delayed_writes 	0 	The number of INSERT DELAYED rows written.
Not_flushed_delayed_rows 	0 	The number of rows waiting to be written in INSERT DELAYED queues.
Begin Key cache Variable 	Value 	Description
Documentation
Key_blocks_not_flushed 	0 	The number of key blocks in the key cache that have changed but haven't yet been flushed to disk. It used to be known as Not_flushed_key_blocks.
Key_blocks_unused 	14 k 	The number of unused blocks in the key cache. You can use this value to determine how much of the key cache is in use.
Key_blocks_used 	0 	The number of used blocks in the key cache. This value is a high-water mark that indicates the maximum number of blocks that have ever been in use at one time.
Key_read_requests 	0 	The number of requests to read a key block from the cache.
Key_reads 	0 	The number of physical reads of a key block from disk. If Key_reads is big, then your key_buffer_size value is probably too small. The cache miss rate can be calculated as Key_reads/Key_read_requests.
Key_write_requests 	0 	The number of requests to write a key block to the cache.
Key_writes 	0 	The number of physical writes of a key block to disk.
Key_buffer_fraction_% 	11.52 % 	
Begin Joins Variable 	Value 	Description
Select_full_join 	0 	The number of joins that do not use indexes. If this value is not 0, you should carefully check the indexes of your tables.
Select_full_range_join 	0 	The number of joins that used a range search on a reference table.
Select_range 	0 	The number of joins that used ranges on the first table. (It's normally not critical even if this is big.)
Select_range_check 	0 	The number of joins without keys that check for key usage after each row. (If this is not 0, you should carefully check the indexes of your tables.)
Select_scan 	80 	The number of joins that did a full scan of the first table.
Begin Replication Variable 	Value 	Description
Show slave hosts Show slave status Documentation
Rpl_status 	NULL 	The status of failsafe replication (not yet implemented).
Slave_open_temp_tables 	0 	The number of temporary tables currently open by the slave SQL thread.
Slave_retried_transactions 	0 	Total (since startup) number of times the replication slave SQL thread has retried transactions.
Slave_running 	OFF 	This is ON if this server is a slave that is connected to a master.
Begin Sorting Variable 	Value 	Description
Sort_merge_passes 	0 	The number of merge passes the sort algorithm has had to do. If this value is large, you should consider increasing the value of the sort_buffer_size system variable.
Sort_range 	0 	The number of sorts that were done with ranges.
Sort_rows 	0 	The number of sorted rows.
Sort_scan 	0 	The number of sorts that were done by scanning the table.
Begin Tables Variable 	Value 	Description
Flush (close) all tables Show open tables
Open_tables 	27 	The number of tables that are open.
Opened_tables 	33 	The number of tables that have been opened. If opened tables is big, your table cache value is probably too small.
Table_locks_immediate 	52 	The number of times that a table lock was acquired immediately.
Table_locks_waited 	0 	The number of times that a table lock could not be acquired immediately and a wait was needed. If this is high, and you have performance problems, you should first optimize your queries, and then either split your table or tables or use replication.
Begin Transaction coordinator Variable 	Value 	Description
Tc_log_max_pages_used 	0 	
Tc_log_page_size 	0 	
Tc_log_page_waits 	0 	
Begin Variable 	Value 	Description
Compression 	OFF 	
Open_files 	54 	The number of files that are open.
Open_streams 	0 	The number of streams that are open (used mainly for logging).
Prepared_stmt_count 	0 	
Uptime_since_flush_status 	122 k 	
Open new phpMyAdmin windowOpen new phpMyAdmin window



Variables and settings...


Server: localhost

    * DatabasesDatabases
    * SQLSQL
    * StatusStatus
    * VariablesVariables
    * CharsetsCharsets
    * EnginesEngines
    * PrivilegesPrivileges
    * ProcessesProcesses
    * ExportExport
    * ImportImport


Server variables and settings
Variable 	Session value / Global value
auto increment increment 	1
auto increment offset 	1
automatic sp privileges 	ON
back log 	50
basedir 	/usr/
binlog cache size 	32,768
bulk insert buffer size 	8,388,608
character set client 	utf8
(Global value) 	latin1
character set connection 	utf8
(Global value) 	latin1
character set database 	latin1
character set filesystem 	binary
character set results 	utf8
(Global value) 	latin1
character set server 	latin1
character set system 	utf8
character sets dir 	/usr/share/mysql/charsets/
collation connection 	utf8_unicode_ci
(Global value) 	latin1_swedish_ci
collation database 	latin1_swedish_ci
collation server 	latin1_swedish_ci
completion type 	0
concurrent insert 	1
connect timeout 	5
datadir 	/var/lib/mysql/
date format 	%Y-%m-%d
datetime format 	%Y-%m-%d %H:%i:%s
default week format 	0
delay key write 	ON
delayed insert limit 	100
delayed insert timeout 	300
delayed queue size 	1,000
div precision increment 	4
keep files on create 	OFF
engine condition pushdown 	OFF
expire logs days 	10
flush 	OFF
flush time 	0
ft boolean syntax 	+ -><()~*:""&|
ft max word len 	84
ft min word len 	4
ft query expansion limit 	20
ft stopword file 	(built-in)
group concat max len 	1,024
have archive 	YES
have bdb 	NO
have blackhole engine 	YES
have compress 	YES
have crypt 	YES
have csv 	YES
have dynamic loading 	YES
have example engine 	NO
have federated engine 	YES
have geometry 	YES
have innodb 	YES
have isam 	NO
have merge engine 	YES
have ndbcluster 	DISABLED
have openssl 	DISABLED
have ssl 	DISABLED
have query cache 	YES
have raid 	NO
have rtree keys 	YES
have symlink 	YES
hostname 	armory
init connect 	
init file 	
init slave 	
innodb additional mem pool size 	1,048,576
innodb autoextend increment 	8
innodb buffer pool awe mem mb 	0
innodb buffer pool size 	8,388,608
innodb checksums 	ON
innodb commit concurrency 	0
innodb concurrency tickets 	500
innodb data file path 	ibdata1:10M:autoextend
innodb data home dir 	
innodb doublewrite 	ON
innodb fast shutdown 	1
innodb file io threads 	4
innodb file per table 	OFF
innodb flush log at trx commit 	1
innodb flush method 	
innodb force recovery 	0
innodb lock wait timeout 	50
innodb locks unsafe for binlog 	OFF
innodb log arch dir 	
innodb log archive 	OFF
innodb log buffer size 	1,048,576
innodb log file size 	5,242,880
innodb log files in group 	2
innodb log group home dir 	./
innodb max dirty pages pct 	90
innodb max purge lag 	0
innodb mirrored log groups 	1
innodb open files 	300
innodb rollback on timeout 	OFF
innodb support xa 	ON
innodb sync spin loops 	20
innodb table locks 	ON
innodb thread concurrency 	8
innodb thread sleep delay 	10,000
interactive timeout 	28,800
join buffer size 	131,072
key buffer size 	16,777,216
key cache age threshold 	300
key cache block size 	1,024
key cache division limit 	100
language 	/usr/share/mysql/english/
large files support 	ON
large page size 	0
large pages 	OFF
lc time names 	en_US
license 	GPL
local infile 	ON
locked in memory 	OFF
log 	OFF
log bin 	OFF
log bin trust function creators 	OFF
log error 	
log queries not using indexes 	OFF
log slave updates 	OFF
log slow queries 	OFF
log warnings 	1
long query time 	10
low priority updates 	OFF
lower case file system 	OFF
lower case table names 	0
max allowed packet 	16,776,192
max binlog cache size 	4,294,967,295
max binlog size 	104,857,600
max connect errors 	10
max connections 	100
max delayed threads 	20
max error count 	64
max heap table size 	16,777,216
max insert delayed threads 	20
max join size 	18446744073709551615
max length for sort data 	1,024
max prepared stmt count 	16,382
max relay log size 	0
max seeks for key 	4,294,967,295
max sort length 	1,024
max sp recursion depth 	0
max tmp tables 	32
max user connections 	0
max write lock count 	4,294,967,295
multi range count 	256
myisam data pointer size 	6
myisam max sort file size 	2,147,483,647
myisam recover options 	OFF
myisam repair threads 	1
myisam sort buffer size 	8,388,608
myisam stats method 	nulls_unequal
ndb autoincrement prefetch sz 	32
ndb force send 	ON
ndb use exact count 	ON
ndb use transactions 	ON
ndb cache check time 	0
ndb connectstring 	
net buffer length 	16,384
net read timeout 	30
net retry count 	10
net write timeout 	60
new 	OFF
old passwords 	OFF
open files limit 	1,024
optimizer prune level 	1
optimizer search depth 	62
pid file 	/var/run/mysqld/mysqld.pid
port 	3,306
preload buffer size 	32,768
profiling 	OFF
profiling history size 	15
protocol version 	10
query alloc block size 	8,192
query cache limit 	1,048,576
query cache min res unit 	4,096
query cache size 	16,777,216
query cache type 	ON
query cache wlock invalidate 	OFF
query prealloc size 	8,192
range alloc block size 	2,048
read buffer size 	131,072
read only 	OFF
read rnd buffer size 	262,144
relay log purge 	ON
relay log space limit 	0
rpl recovery rank 	0
secure auth 	OFF
secure file priv 	
server id 	0
skip external locking 	ON
skip networking 	OFF
skip show database 	OFF
slave compressed protocol 	OFF
slave load tmpdir 	/tmp/
slave net timeout 	3,600
slave skip errors 	OFF
slave transaction retries 	10
slow launch time 	2
socket 	/var/run/mysqld/mysqld.sock
sort buffer size 	2,097,144
sql big selects 	ON
sql mode 	
sql notes 	ON
sql warnings 	OFF
ssl ca 	
ssl capath 	
ssl cert 	
ssl cipher 	
ssl key 	
storage engine 	MyISAM
sync binlog 	0
sync frm 	ON
system time zone 	CST
table cache 	64
table lock wait timeout 	50
table type 	MyISAM
thread cache size 	8
thread stack 	131,072
time format 	%H:%i:%s
time zone 	SYSTEM
timed mutexes 	OFF
tmp table size 	33,554,432
tmpdir 	/tmp
transaction alloc block size 	8,192
transaction prealloc size 	4,096
tx isolation 	REPEATABLE-READ
updatable views with limit 	YES
version 	5.0.51a-3ubuntu5.4
version comment 	(Ubuntu)
version compile machine 	i486
version compile os 	debian-linux-gnu
wait timeout 	28,800
Open new phpMyAdmin windowOpen new phpMyAdmin window


I have no idea what to do.  Any help would be appreciated!

---

