---
title: "Percona and my.cnf"
date: 2013-01-23
forum: Server Platforms
---

### Post by Bright Hammer on 2013-01-23
Hi Everyone, I recently setup server running 12.04,Nginx,Percona and php. Everything was working great until i did a search and found a bunch of mysql-bin files taking up 27G of space. (FYI i have a basic percona install and did not configure my.cnf)Checked with google and it says to edit you my.cnf. Well percona dose not crate the file by default so this bring me to question 1. Ok read up on creating a my.cnf and use the config wizard over at tool.percona.com to create one. Copied it over and rebooted the server. At boot i got error couldn't connect to the database so i renamed the file and things started working again. This brings me to question 2. I know this might not be the right area for this but any help would be appreciated.


Questions- 

1. Since Percona doesn't create a my.cnf what is Percona using for its config?

2. How do i enable the my.cnf on a Percona server followed by how to verify it is using the my.cnf i created.

---

### Post by rubylaser on 2013-01-23
1. Percona has default values that it uses until you supply a config file.
2. You need to put your file at /etc/my.cnf rather than /etc/mysql/my.cnf for Percona to use it.

You could change some values in your my.cnf and then restart and verify that they've changed via the mysqltuner perl script..
```
wget http://mysqltuner.com/mysqltuner.pl
```

As a caution, some of the file paths that the Percona my.cnf creator script makes, won't exist by default.  Here's what I use on my server.

```

[mysql]

# CLIENT #
port                           = 3306
socket                         = /var/run/mysqld/mysqld.sock

[mysqld]

# GENERAL #
user                           = mysql
default_storage_engine         = InnoDB
socket                         = /var/run/mysqld/mysqld.sock

# MyISAM #
key_buffer_size                = 32M
myisam_recover                 = FORCE,BACKUP

# SAFETY #
max_allowed_packet             = 16M
max_connect_errors             = 1000000
skip_name_resolve

# DATA STORAGE #
#datadir                        = /var/lib/mysql/data/

# BINARY LOGGING #
log_bin                        = mysql-bin
expire_logs_days               = 14
sync_binlog                    = 1

# CACHES AND LIMITS #
tmp_table_size                 = 32M
max_heap_table_size            = 32M
query_cache_type               = 0
query_cache_size           = 8M
#table_cache               = 4096
max_connections                = 500
thread_cache_size              = 50
open_files_limit               = 65535
table_definition_cache         = 1024
table_open_cache               = 4096
max_allowed_packet         = 12582912
group_concat_max_len           = 8192


# INNODB #
innodb_flush_method            = O_DIRECT
innodb_log_files_in_group      = 2
#innodb_log_file_size           = 128M
innodb_flush_log_at_trx_commit = 1
innodb_file_per_table          = 1
innodb_buffer_pool_size        = 2G

# LOGGING #
log_error                      = /var/lib/mysql/data/mysql-error.log
log_queries_not_using_indexes  = 1
slow_query_log                 = 1
slow_query_log_file            = /var/lib/mysql/data/mysql-slow.log
```

---

### Post by Bright Hammer on 2013-01-23
Thanks for your help rubylaser!

I copied your my.cnf to the /etc/my.cnf and rebooted the server. When I try to log in to sql I get a socket error. So I know it is using the my.cnf but I am lost at to what to modify in the my.cnf.

Is there a way for me to see the the current non-my.cnf config the percona server is currently using?

I was doing some snooping around and found a debian.cnf wich says its not to be modified. But it looks to contain the server config. Could this be the default percona config file?

# Automatically generated for Debian scripts. DO NOT TOUCH!
[client]
host     = localhost
user     = debian-sys-maint
password = xYzK9qi0NK9OaeYI
socket   = /var/run/mysqld/mysqld.sock
[mysql_upgrade]
host     = localhost
user     = debian-sys-maint
password = xYzK9qi0NK9OaeYI
socket   = /var/run/mysqld/mysqld.sock
basedir  = /usr

The whole reason I want to know where the current config is because i have 27G in mysql-bin files on my server. Currently when i do a purge binary logs the query completes ok but it dosn't delete the files. I am on a vps and if it gets any bigger i will need to buy more space.

Thanks for you help again!

---

