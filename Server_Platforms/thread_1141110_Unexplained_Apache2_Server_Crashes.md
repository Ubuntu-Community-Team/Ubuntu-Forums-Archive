---
title: "Unexplained Apache2 Server Crashes"
date: 2009-04-28
forum: Server Platforms
---

### Post by Rhiknow on 2009-04-28
Greetings,

My Apache2 server (Ubuntu 8.10, 2.6.27-7-server, AMD Sempron 2400+, i686) keeps stopping intermittently. I can ssh in fine, it's just it stops serving webpages. I have to type in: 'sudo apache2ctl start' and enter my SSL password to get her back up-and-running again.

It happens about once every day or two.

I have no idea where to start. In the mean time, I have a cron job running every hour that restarts the Apache2 server. This is a far from ideal solution.

I haven't got anything fancy running. All it's doing at the moment is serving a few webpages and handling my email.

I'm completely stumped. Anyone have any suggestions? 

Many thanks in advance,

Rhik

---

### Post by terazen on 2009-04-28
Have you checked logfiles and memory usages?  I had a problem a while back where a Drupal/Moodle (i forget which) cronjob was causing high memory usage.

How I figured it out was to watch the memory usage of apache and when the problem happened trace it back to the cronjob that ran at that time of the day.

---

### Post by luk.sa on 2009-04-28
Any luck looking into /var/log/apache2/error.log?

You should see some event before the server crashes. Also check the access.log it might tell you which app causes the crash

---

### Post by Rhiknow on 2009-04-29
Hi thanks for the suggestion. Here's the error log:

[Sun Apr 26 06:55:52 2009] [notice] Apache/2.2.9 (Ubuntu) mod_ssl/2.2.9 OpenSSL/0.9.8g configured -- resuming normal operations
[Sun Apr 26 07:52:54 2009] [error] [client 86.44.18.69] File does not exist: /home/prestocab/prestocab.com/secure/favicon.ico
[Sun Apr 26 07:52:57 2009] [error] [client 86.44.18.69] File does not exist: /home/prestocab/prestocab.com/secure/favicon.ico
[Sun Apr 26 09:51:35 2009] [error] [client 86.44.18.69] File does not exist: /home/xlhi/xlhi.com/www/favicon.ico
[Sun Apr 26 09:51:38 2009] [error] [client 86.44.18.69] File does not exist: /home/xlhi/xlhi.com/www/favicon.ico
[Sun Apr 26 09:52:04 2009] [error] [client 61.125.203.95] File does not exist: /home/xlhi/xlhi.com/www/favicon.ico, referer: [http://www.xlhi.com/peter/](http://www.xlhi.com/peter/)
[Sun Apr 26 13:29:47 2009] [error] [client 96.227.152.88] File does not exist: /home/xlhi/xlhi.com/www/favicon.ico
[Sun Apr 26 14:15:32 2009] [error] [client 66.249.71.36] File does not exist: /home/xlhi/xlhi.com/www/robots.txt
[Sun Apr 26 14:15:32 2009] [error] [client 66.249.71.36] File does not exist: /home/xlhi/xlhi.com/www/iseq.png
[Sun Apr 26 15:56:40 2009] [error] [client 219.234.81.33] File does not exist: /home/xlhi/xlhi.com/www/robots.txt
[Sun Apr 26 16:39:44 2009] [error] [client 66.249.71.113] File does not exist: /home/prestocab/prestocab.com/secure/robots.txt
[Sun Apr 26 18:06:14 2009] [error] [client 74.6.18.244] File does not exist: /home/xlhi/xlhi.com/www/robots.txt
[Tue Apr 28 06:17:35 2009] [error] (2)No such file or directory: Cannot create SSLMutex with file `/var/run/apache2/ssl_mutex'
Configuration Failed
[Tue Apr 28 06:18:22 2009] [notice] Apache/2.2.9 (Ubuntu) mod_ssl/2.2.9 OpenSSL/0.9.8g configured -- resuming normal operations
[Tue Apr 28 12:44:36 2009] [error] [client 66.249.71.113] File does not exist: /home/prestocab/prestocab.com/secure/robots.txt
[Tue Apr 28 13:19:05 2009] [error] [client 195.128.18.18] File does not exist: /home/xlhi/xlhi.com/www/robots.txt
[Tue Apr 28 13:19:06 2009] [error] [client 195.128.18.18] File does not exist: /home/xlhi/xlhi.com/www/sitemap
[Tue Apr 28 13:19:06 2009] [error] [client 195.128.18.18] File does not exist: /home/xlhi/xlhi.com/www/sitemap.xml
[Tue Apr 28 13:19:06 2009] [error] [client 195.128.18.18] File does not exist: /home/xlhi/xlhi.com/www/google_sitemap.xml
[Wed Apr 29 05:55:14 2009] [notice] Apache/2.2.9 (Ubuntu) mod_ssl/2.2.9 OpenSSL/0.9.8g configured -- resuming normal operations

What are these ssl mutex errors?

Many thanks in advance,

---

### Post by terazen on 2009-04-29
Does /var/run/apache2 exist?

Also when the server crashes, what is the cpu/memory used by apache processes?

---

### Post by Rhiknow on 2009-04-29
> **terazen said:**
> Does /var/run/apache2 exist?

Also when the server crashes, what is the cpu/memory used by apache processes?

Hi, thanks for the suggestion.

It's just happened again. I'm using roundcube email and postfix that runs off a MySQL database. I also have to do a "sudo /etc/init.d/mysql start" each time my server crashes to get it re-starting.

The answer is, I don't know to check the cpu/memory info! How can I find out the cpu/memory? Here's a 'top' dump:

top - 15:22:58 up  2:44,  1 user,  load average: 0.00, 0.00, 0.00
Tasks: 101 total,   1 running, 100 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    497876k total,   315344k used,   182532k free,    42160k buffers
Swap:  2097136k total,        0k used,  2097136k free,   104568k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7179 prestoca  20   0  2412 1136  884 R  0.3  0.2   0:00.04 top
    1 root      20   0  3056 1884  564 S  0.0  0.4   0:01.53 init
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.09 ksoftirqd/0
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.03 events/0
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 khelper
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.03 kblockd/0
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
  110 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue
  114 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
  154 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  155 root      20   0     0    0    0 S  0.0  0.0   0:00.06 pdflush
  156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0

---

### Post by Rhiknow on 2009-04-29
> **terazen said:**
> Does /var/run/apache2 exist?


No.

---

