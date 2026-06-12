---
title: "Help with reducing memory usage of Mail Server, particularly mysql"
date: 2013-12-13
forum: Server Platforms
---

### Post by CharlesA on 2013-12-13
Howdy,

I've got a mail server setup on a 512MB VPS and it seems to want to eat swap space for lunch.

I am running Dovecot, Postfix, MariaDB and spamassassin on it, and I wanted to know what I can do it help reduce the memory footprint I am leaving.

Here's the memory usage now:

```
free -m
             total       used       free     shared    buffers     cached
Mem:           512        439         72          0          0        101
-/+ buffers/cache:        337        174
Swap:          512        144        367

```

What concerns me is the number of mysql processes shown in htop. I think this is due to the max_connections variable being set to 100 in /etc/mysql/my.cnf:

```
max_connections         = 100
connect_timeout         = 5
wait_timeout            = 600
max_allowed_packet      = 16M
thread_cache_size       = 128
sort_buffer_size        = 4M
bulk_insert_buffer_size = 16M
tmp_table_size          = 32M
max_heap_table_size     = 32M

```

Any thoughts on how this should be configured for low(er) memory usage?

I did find a few posts ([one]("http://xenforo.com/community/threads/optimal-settings-for-vps-with-512mb-ram-memory-issue.47686/"), [two]("http://rudd-o.com/linux-and-free-software/tuning-a-mysql-server-in-5-minutes")) on mysql/mariadb configuration to lower memory usage, but I'm not really sure what each change is supposed to do. The server is running fine now, I just want to get the swap usage down, if I can.

As of now, I am using the defaults MariaDB shipped with.

Thanks for any help with this.

---

### Post by nerdtron on 2013-12-14
I think that would be normal since you run a database with your mail server. Plus you have spamassassin too. Do you have clamAV too?
On our old mail server using sendmail, plus squirrelmail and not using any database for users, the free memory is less than 50 MB (512MB RAM). Although is uses a little less swap, it still uses swap. I guess yours is acceptable.

---

### Post by CharlesA on 2013-12-14
> **nerdtron said:**
> I think that would be normal since you run a database with your mail server. Plus you have spamassassin too. Do you have clamAV too?
On our old mail server using sendmail, plus squirrelmail and not using any database for users, the free memory is less than 50 MB (512MB RAM). Although is uses a little less swap, it still uses swap. I guess yours is acceptable.

Yeah, I'm running the whole AV and all the other stuff on it.

I was messing around with the innoDB memory allocations and reduced them quite a bit, so I think the main thing that is using memory is mysql.

It looks like I'm going to need to do more digging.

Here's what the original settings for InnoDB were:

```
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
default_storage_engine  = InnoDB
# you can't just change log file size, requires special procedure
#innodb_log_file_size   = 50M
innodb_buffer_pool_size = 256M
innodb_log_buffer_size  = 8M
innodb_file_per_table   = 1
innodb_open_files       = 400
innodb_io_capacity      = 400
innodb_flush_method     = O_DIRECT

```

This is what I changed them to, but I have no idea if they can go any lower or not as I just started splitting the memory in half to see what would happen.

```
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
default_storage_engine  = InnoDB
# you can't just change log file size, requires special procedure
#innodb_log_file_size   = 50M
innodb_buffer_pool_size = 64M
innodb_log_buffer_size  = 2M
innodb_file_per_table   = 1
innodb_open_files       = 400
innodb_io_capacity      = 400
innodb_flush_method     = O_DIRECT

```

---

