---
title: "[SOLVED] Apache2: Cannot allocate memory"
date: 2008-05-27
forum: Server Platforms
---

### Post by turboraketti on 2008-05-27
I just had myself a VPS machine at a web hotel, got it set up with Ubuntu 8.04 server. To start with I "apt-get install apache2". However, I can't start it with "apache2ctl start" -- there are no apache|httpd in the process list and this is what I see in /var/logs/apache2/error.log:
```
[Tue May 27 14:45:53 2008] [warn] pid file /var/run/apache2.pid overwritten -- Unclean shutdown of previous Apache run?
[Tue May 27 14:45:53 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Tue May 27 14:45:53 2008] [alert] (12)Cannot allocate memory: apr_thread_create: unable to create worker thread
[Tue May 27 14:45:53 2008] [emerg] (22)Invalid argument: ap_queue_info_set_idle failed. Attempting to shutdown process gracefully.
[Tue May 27 14:45:53 2008] [alert] (12)Cannot allocate memory: apr_thread_create: unable to create worker thread
[Tue May 27 14:45:55 2008] [alert] No active workers found... Apache is exiting!
```
I don't seem to sort it out. Can someone point me in the right direction?

---

### Post by turboraketti on 2008-05-27
Answering myself here... Did quite some googling and found out that apache2 is eating quite some memory in its default behaviour. I looked in /proc/user_beancounters and found that there was a number of failures on the privvmpages line. If I was the administrator on the physical machine I could have done:
```
vzctl set 1 --privvmpages 100000 --save
```
Since I'm not able to make such modifications, I can modify apache's behaviour to use much less memory by doing this:
```
sudo apt-get install apache2-mpm-prefork
```
as suggested by Yogarine in [[COLOR="DarkOliveGreen"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=117073") (where also other possible solutions are mentioned).

My VPS has 128MB and apache2 is now running like a charm.

Hope this helps someone. :)

---

### Post by parren on 2008-06-26
It did! Thanks.
-parren

---

### Post by jrhurley on 2010-01-31
Just spent the last day desperately trying to sort this... your answer solved it in seconds! Thanks! (from a very grateful and now exhausted man!)

---

