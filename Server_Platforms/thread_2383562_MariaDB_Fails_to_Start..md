---
title: "MariaDB Fails to Start."
date: 2018-01-26
forum: Server Platforms
---

### Post by acascianelli on 2018-01-26
Running Ubuntu Server 17.10 with all latest patches.

I've been running a Apache HTTPD web server with MariaDB hosting TTRSS.  It's been working fine for about a week up until yesterday when MariaDB suffered a crash and now it won't come back up.  Here is what the error log looks like:

```
018-01-26 19:22:17 140354563878848 [Note] InnoDB: innodb_empty_free_list_algorithm has been changed to legacy because of small buffer pool size. In order to use backoff, increase buffer pool at least up to 20MB.

2018-01-26 19:22:18 140354563878848 [Note] InnoDB: Using mutexes to ref count buffer pool pages
2018-01-26 19:22:18 140354563878848 [Note] InnoDB: The InnoDB memory heap is disabled
2018-01-26 19:22:18 140354563878848 [Note] InnoDB: Mutexes and rw_locks use GCC atomic builtins
2018-01-26 19:22:18 140354563878848 [Note] InnoDB: GCC builtin __atomic_thread_fence() is used for memory barrier
2018-01-26 19:22:18 140354563878848 [Note] InnoDB: Compressed tables use zlib 1.2.11
2018-01-26 19:22:18 140354563878848 [Note] InnoDB: Using Linux native AIO
2018-01-26 19:22:18 140354563878848 [Note] InnoDB: Using generic crc32 instructions
2018-01-26 19:22:18 140354563878848 [Note] InnoDB: Initializing buffer pool, size = 128.0M
2018-01-26 19:22:18 140354563878848 [Note] InnoDB: Completed initialization of buffer pool
2018-01-26 19:22:18 140354563878848 [Note] InnoDB: Highest supported file format is Barracuda.
2018-01-26 19:22:18 140354563878848 [Note] InnoDB: Starting crash recovery from checkpoint LSN=129135088
2018-01-26 19:22:18 140354563878848 [Note] InnoDB: Restoring possible half-written data pages from the doublewrite buffer...
InnoDB: Set innodb_force_recovery to ignore this error.
2018-01-26 19:22:18 140354563878848 [ERROR] Plugin 'InnoDB' init function returned error.
2018-01-26 19:22:18 140354563878848 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
2018-01-26 19:22:18 140354563878848 [Note] Plugin 'FEEDBACK' is disabled.
2018-01-26 19:22:18 140354563878848 [ERROR] Unknown/unsupported storage engine: InnoDB
2018-01-26 19:22:18 140354563878848 [ERROR] Aborting

Error in my_thread_global_end(): 1 threads didn't exit
```

---

### Post by acascianelli on 2018-01-26
I was able to get MariaDB started in recovery mode just good enough to take a backup of my TTRSS database.

---

### Post by LHammonds on 2018-01-27
#1 - When you setup a database server, always make sure you have an automated backup job running that will dump all your databases to .sql files.  Check my sig on how I do it.

#2 - Unless you are testing and giving feedback for bleeding edge releases (like the odd-number versions 17.xx), I'd suggest sticking to the even-numbered stable releases (16.04 LTS...LTS = Long Term Support)

#3 - If you got the backup .sql files, uninstall / purge MariaDB and re-install it.  Then restore the databases from the .sql files.

LHammonds

---

### Post by acascianelli on 2018-01-29
> **LHammonds said:**
> #1 - When you setup a database server, always make sure you have an automated backup job running that will dump all your databases to .sql files.  Check my sig on how I do it.

#2 - Unless you are testing and giving feedback for bleeding edge releases (like the odd-number versions 17.xx), I'd suggest sticking to the even-numbered stable releases (16.04 LTS...LTS = Long Term Support)

#3 - If you got the backup .sql files, uninstall / purge MariaDB and re-install it.  Then restore the databases from the .sql files.

LHammonds

#1 It was on my todo list, just didn't get around to it yet.
#2 This is a personal home server, and I like bleeding edge releases.
#3 I did manage to get MariaDB running in recovery mode to the point where I could take a backup, but when I tried dumping and recreating the database it was completely corrupted.  I got mad, uninstalled MariaDB and installed PostgreSQL and started from scratch.  TTRSS recommends PostgreSQL anyway.

Once if the first things I did after getting the database up and running again under PostgreSQL was setup a backup job.

---

### Post by LHammonds on 2018-01-30
> **acascianelli said:**
> I like bleeding edge releases.
> **acascianelli said:**
> I got mad, uninstalled MariaDB
Not sure if the issue was the application causing corruption or MariaDB was just too bleeding edge or if the service wasn't shutdown properly during reboots...but you sound conflicted about bleeding edge. ;)

> **acascianelli said:**
> Once if the first things I did after getting the database up and running again under PostgreSQL was setup a backup job.

Awesome, now you have one of these:
[IMG]https://jbburrows.files.wordpress.com/2010/08/round-tuit.jpg[/IMG]

When you dumped the backup to .sql files, did you look to see if the .sql backup files looked ok?  They should be human-readable SQL commands (and not empty or binary files)

LHammonds

---

### Post by acascianelli on 2018-01-30
It did, but after importing the database TTRSS was not happy and was throwing a ton of errors.

---

