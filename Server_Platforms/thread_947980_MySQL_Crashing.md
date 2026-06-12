---
title: "MySQL Crashing"
date: 2008-10-14
forum: Server Platforms
---

### Post by Arieder on 2008-10-14
Hey guys, basically my problem is each time I try to start mysql, I get:

> 
081014 19:57:02  InnoDB: Started; log sequence number 0 243175184
081014 19:57:02 [Note] Recovering after a crash using /var/log/mysql/mysql-bin
081014 19:57:02 [Note] Starting crash recovery...
081014 19:57:02 [Note] Crash recovery finished.
081014 19:57:02 - mysqld got signal 11;
This could be because you hit a bug. It is also possible that this binary
or one of the libraries it was linked against is corrupt, improperly built,
or misconfigured. This error can also be caused by malfunctioning hardware.
We will try our best to scrape up some info that will hopefully help diagnose
the problem, but since we have already crashed, something is definitely wrong
and this may fail.

key_buffer_size=16777216
read_buffer_size=131072
max_used_connections=0
max_connections=100
threads_connected=0
It is possible that mysqld could use up to 
key_buffer_size + (read_buffer_size + sort_buffer_size)*max_connections = 233983 K
bytes of memory
Hope that's ok; if not, decrease some variables in the equation.

thd=0x8b01660
Attempting backtrace. You can use the following information to find out
where mysqld died. If you see no messages after this, something went
terribly wrong...
Cannot determine thread, fp=0xbf9b0f88, backtrace may not be correct.
Stack range sanity check OK, backtrace follows:
0x81ea513
0x823066a
0x82284bb
0x8229a5e
0x822a254
0x822a53f
0x8281548
0x82826ca
0x81ecec1
0xb7c62ebc
0x8160581
New value of fp=(nil) failed sanity check, terminating stack trace!
Please read [http://dev.mysql.com/doc/mysql/en/using-stack-trace.html](http://dev.mysql.com/doc/mysql/en/using-stack-trace.html) and follow instructions on how to resolve the stack trace. Resolved
stack trace is much more helpful in diagnosing the problem, so please do 
resolve it
Trying to get some variables.
Some pointers may be invalid and cause the dump to abort...
thd->query at (nil)  is invalid pointer
thd->thread_id=1903393133
The manual page at [http://www.mysql.com/doc/en/Crashing.html](http://www.mysql.com/doc/en/Crashing.html) contains
information that should help you find out what is causing the crash.


Now mysql was working FINE before....no idea what the problem is :(, right now I have it running with "mysqld --skip-grant-tables --user=root", however I cant access the user table without the connection being broken again....please help.

Oh, and here is the message I get when using the skip grant tables command:

> 
081014 19:57:10  InnoDB: Started; log sequence number 0 243175184
081014 19:57:10 [Note] Recovering after a crash using /var/log/mysql/mysql-bin
081014 19:57:10 [Note] Starting crash recovery...
081014 19:57:10 [Note] Crash recovery finished.
081014 19:57:10 [Note] mysqld: ready for connections.
Version: '5.0.38-Ubuntu_0ubuntu1.4-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Ubuntu 7.04 distribution


Thankyou.

---

### Post by Arieder on 2008-10-14
I believe the "mysql" database is corrupted as I can access EVERYTHING however if I try to access the user table or update it using a query mysql crashes....any solutions? I wish I could find a way to have sql re-create the mysql database...

---

