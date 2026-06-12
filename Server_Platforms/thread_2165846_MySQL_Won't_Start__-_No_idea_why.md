---
title: "MySQL Won't Start  - No idea why"
date: 2013-08-06
forum: Server Platforms
---

### Post by Hexxus on 2013-08-06
Hey everyone, here's the deal, got a call last night that our ESX host was down, some how the server was powered off, turned it on and started the virtual machines everything looked fine.

Wrong, My mysql server 12.04LTS won't startup:

If I do ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo /etc/init.d/mysql restart[/FONT][/COLOR]
```  Then I get:  

```
start: Job failed to start
```

Here is what the logs look like:

```
130806 13:02:01  InnoDB: Page checksum 2360990246, prior-to-4.0.14-form checksum 849003906
InnoDB: stored checksum 2210709444, prior-to-4.0.14-form stored checksum 3217443162
InnoDB: Page lsn 0 1595882116, low 4 bytes of lsn at page end 1595882116
InnoDB: Page number (if stored to page already) 26885,
InnoDB: space id (if created with >= MySQL-4.1.1 and stored already) 0
InnoDB: Database page corruption on disk or a failed
InnoDB: file read of page 52.
InnoDB: You may have to recover from a backup.
InnoDB: It is also possible that your operating
InnoDB: system has corrupted its own file cache
InnoDB: and rebooting your computer removes the
InnoDB: error.
InnoDB: If the corrupt page is an index page
InnoDB: you can also try to fix the corruption
InnoDB: by dumping, dropping, and reimporting
InnoDB: the corrupt table. You can use CHECK
InnoDB: TABLE to scan your table for corruption.
InnoDB: See also http://dev.mysql.com/doc/refman/5.5/en/forcing-innodb-recovery.html
InnoDB: about forcing recovery.
InnoDB: Error: trying to access page number 8241156 in space 0,
InnoDB: space name ./ibdata1,
InnoDB: which is outside the tablespace bounds.
InnoDB: Byte offset 0, len 16384, i/o type 10.
InnoDB: If you get this error at mysqld startup, please check that
InnoDB: your my.cnf matches the ibdata files that you have in the
InnoDB: MySQL server.
130806 13:02:01  InnoDB: Assertion failure in thread 140448854886208 in file fil0fil.c line 4579
InnoDB: We intentionally generate a memory trap.
InnoDB: Submit a detailed bug report to http://bugs.mysql.com.
InnoDB: If you get repeated assertion failures or crashes, even
InnoDB: immediately after the mysqld startup, there may be
InnoDB: corruption in the InnoDB tablespace. Please refer to
InnoDB: http://dev.mysql.com/doc/refman/5.5/en/forcing-innodb-recovery.html
InnoDB: about forcing recovery.
18:02:01 UTC - mysqld got signal 6 ;
This could be because you hit a bug. It is also possible that this binary
or one of the libraries it was linked against is corrupt, improperly built,
or misconfigured. This error can also be caused by malfunctioning hardware.
We will try our best to scrape up some info that will hopefully help
diagnose the problem, but since we have already crashed, 
something is definitely wrong and this may fail.


key_buffer_size=16777216
read_buffer_size=131072
max_used_connections=0
max_threads=151
thread_count=0
connection_count=0
It is possible that mysqld could use up to 
key_buffer_size + (read_buffer_size + sort_buffer_size)*max_threads = 346685 K  bytes of memory
Hope that's ok; if not, decrease some variables in the equation.


Thread pointer: 0x0
Attempting backtrace. You can use the following information to find out
where mysqld died. If you see no messages after this, something went
terribly wrong...
stack_bottom = 0 thread_stack 0x30000
/usr/sbin/mysqld(my_print_stacktrace+0x29)[0x7fbcce399349]
/usr/sbin/mysqld(handle_fatal_signal+0x483)[0x7fbcce25ef33]
/lib/x86_64-linux-gnu/libpthread.so.0(+0xfcb0)[0x7fbcccfaacb0]
/lib/x86_64-linux-gnu/libc.so.6(gsignal+0x35)[0x7fbccc616425]
/lib/x86_64-linux-gnu/libc.so.6(abort+0x17b)[0x7fbccc619b8b]
/usr/sbin/mysqld(+0x6762e2)[0x7fbcce4b92e2]
/usr/sbin/mysqld(+0x651555)[0x7fbcce494555]
/usr/sbin/mysqld(+0x65202c)[0x7fbcce49502c]
/usr/sbin/mysqld(+0x6418b6)[0x7fbcce4848b6]
/usr/sbin/mysqld(+0x61d4bc)[0x7fbcce4604bc]
/usr/sbin/mysqld(+0x612f57)[0x7fbcce455f57]
/usr/sbin/mysqld(+0x613cec)[0x7fbcce456cec]
/usr/sbin/mysqld(+0x615693)[0x7fbcce458693]
/usr/sbin/mysqld(+0x601e6a)[0x7fbcce444e6a]
/usr/sbin/mysqld(+0x5cba29)[0x7fbcce40ea29]
/usr/sbin/mysqld(_Z24ha_initialize_handlertonP13st_plugin_int+0x41)[0x7fbcce261601]
/usr/sbin/mysqld(+0x30b581)[0x7fbcce14e581]
/usr/sbin/mysqld(_Z11plugin_initPiPPci+0xa94)[0x7fbcce151ba4]
/usr/sbin/mysqld(+0x284796)[0x7fbcce0c7796]
/usr/sbin/mysqld(_Z11mysqld_mainiPPc+0x59b)[0x7fbcce0caf3b]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7fbccc60176d]
/usr/sbin/mysqld(+0x27e2c5)[0x7fbcce0c12c5]
The manual page at http://dev.mysql.com/doc/mysql/en/crashing.html contains
information that should help you find out what is causing the crash.

```

The log is quite large with page dumps in it as well, above that it seemed the information I pasted was repeated. 

Thank you everyone!

---

### Post by Hexxus on 2013-08-06
Also - I tried doing a force innodb 0-6 and that didn't affect it at all as suggested in [COLOR=#000000][FONT=Ubuntu Mono]http://dev.mysql.com/doc/refman/5.5/en/forcing-innodb-recovery.html [/FONT][/COLOR]

---

### Post by CharlesA on 2013-08-06
Do you have a backup database you can try restoring?

---

### Post by Hexxus on 2013-08-06
Here's the kicker, no. The server was missed in the backup jobs that we run on our virtual hosts and a cron job wasn't setup.  Otherwise things would've been pretty easy, the server was configured for innodb, so the innodb1 file has the information. Unfortunately it appears thats the file that is corrupt and we cannot get the thing to go due to the corruption.

---

### Post by CharlesA on 2013-08-06
> **Hexxus said:**
> Here's the kicker, no. The server was missed in the backup jobs that we run on our virtual hosts and a cron job wasn't setup.  Otherwise things would've been pretty easy, the server was configured for innodb, so the innodb1 file has the information. Unfortunately it appears thats the file that is corrupt and we cannot get the thing to go due to the corruption.

Damn. Have you tried putting the database on another server and seeing if it will start? If you've already tried a repair (which it looks like you did). I think you might need to start from scratch. :(

---

