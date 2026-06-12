---
title: "innodb and MySQL"
date: 2007-06-24
forum: Server Platforms
---

### Post by Scott07 on 2007-06-24
I guess I am right in thinking that the version of mySQL that you can get with apt does not support innodb?  As far as I can tell my config file is set up to allow innodb to run nicley, I have turned on NO_ENGINE_SUBSTITUTION and mysql insists that innodb is disabled or not compiled.  Anyone have any ideas if there is a simple way to get it working as I have an operational db, I really want to avoid the fuffing about with compiling it and whatnot.

---

### Post by Brazen on 2007-06-24
hmm, I'm using Ubuntu Dapper for our MySQL server at work.  I just installed from the repos and didn't change anything in the config file except for the "old_password" option (set it to 0, not that it matters to your situation).  I always use innodb and have not had a single problem.

---

### Post by Scott07 on 2007-06-25
The config file I am using is:

[client]
#password	= your_password
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

# Here follows entries for some specific programs

[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

skip-innodb_fast_shutdown

# The MySQL server
[mysqld]
user		= mysql
port		= 3306
socket		= /var/run/mysqld/mysqld.sock
datadir		= /var/lib/mysql
tmpdir		= /tmp
#skip-locking
key_buffer = 650M
max_allowed_packet = 1M
table_cache = 512
sort_buffer_size = 8M
read_buffer_size = 8M
read_rnd_buffer_size = 32M
myisam_sort_buffer_size = 200M
thread_cache_size = 16
query_cache_size = 64M
# Try number of CPU's*2 for thread_concurrency
thread_concurrency = 4

ft_min_word_len=3
#ft_stopword_file=/etc/mysql/stopword

sql-mode="STRICT_TRANS_TABLES,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"

# Replication Master Server (default)
# binary logging is required for replication
log-bin=mysql-bin

# required unique id between 1 and 2^32 - 1
# defaults to 1 if master-host is not set
# but will not function as a master if omitted
server-id	= 1


# Uncomment the following if you are using InnoDB tables
innodb_data_home_dir = /var/lib/mysql/
innodb_data_file_path = ibdata1:10M;ibdata2:10M:autoextend
innodb_log_group_home_dir = /var/lib/mysql/
innodb_log_arch_dir = /var/lib/mysql/
# You can set .._buffer_pool_size up to 50 - 80 %
# of RAM but beware of setting memory usage too high
innodb_buffer_pool_size = 384M
innodb_additional_mem_pool_size = 10M
# Set .._log_file_size to 25 % of buffer pool size
innodb_log_file_size = 100M
innodb_log_buffer_size = 8M
innodb_flush_log_at_trx_commit = 1
innodb_lock_wait_timeout = 50

[mysqldump]
quick
max_allowed_packet = 16M

[mysql]
no-auto-rehash
# Remove the next comment character if you are not familiar with SQL
#safe-updates

[isamchk]
key_buffer = 256M
sort_buffer_size = 256M
read_buffer = 2M
write_buffer = 2M

[myisamchk]
key_buffer = 512M
sort_buffer_size = 300M
read_buffer = 8M
write_buffer = 8M

[mysqlhotcopy]
interactive-timeout

---

### Post by Scott07 on 2007-06-25
I have found the problem now and sorted it.  For anyone else who is having this problem I shall explain.  

The sources on the Ubuntu server CD does come with mysql, however its a version that does not have innodb built in.  As the server will always use the CD where possible you dont ever get a version that does have innodb.  If you go into /etc/apt/sources.list and comment out the first source which is the cd, save the file, remove mysql through apt.  Clean out your apt cache and make sure you run an update to get the latest build.  You can then use apt to re install mysql, this time it will use a download source which does have innodb.  If you have used the default config options and data directories then your can get your server running again straight away with no need to re create your databases (but thats not an excuse to no backup first just incase).

Hope this helps anyone who has the same problem.

---

### Post by Scott07 on 2007-06-25
Right the solution above does not actually work, it just destroys your data, ubuntu has to be the worst operating system to use mysql with, the BSD unix operating systems are child's play compared to the difficulty I had had so far.  Finally I am just going to format it and start again, thanks a lot for making things 1000 times more difficult.

---

