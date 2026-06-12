---
title: "php-fpm unidentified high IO"
date: 2018-08-27
forum: Server Platforms
---

### Post by Zolcsi on 2018-08-27
Hi everyone!

I really need some helpp figuring out the bottleneck on my server.
I upgraded it to 18.04 from 14.04, including mysql upgrade from 5.6 to 5.7.
After the upgrade the server got slower, I tracked it down to MySQL, somehow it deleted the old config file and installed the default one, and MySQL got significantly slower. I managed to tune it a bit so it was better, but still not that good. After that I realised that my server was running a very old kernel, so I upgraded it to a current one. Since then I am facing issues with my IO. From time to time IO usage of the disk jumps to 100%. PHP-FPM is using it, but I don't know how or why. And after some time it goes back to normal again.
But I can't seem to figure out what is causing the high IO load.
example output of iotop:
```

Total DISK READ :       3.20 M/s | Total DISK WRITE :      71.51 K/s
Actual DISK READ:       2.43 M/s | Actual DISK WRITE:    1334.85 K/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND    
 6802 be/4 ingatlan    0.00 B/s    0.00 B/s  0.00 % 98.19 % php-fpm: pool ingatlan
 7238 be/4 ingatlan    0.00 B/s    0.00 B/s  0.00 % 97.88 % php-fpm: pool ingatlan
 7033 be/4 ingatlan    0.00 B/s    0.00 B/s  0.00 % 97.19 % php-fpm: pool ingatlan
 7107 be/4 ingatlan    0.00 B/s    0.00 B/s  0.00 % 97.12 % php-fpm: pool ingatlan
 7227 be/4 ingatlan    0.00 B/s    0.00 B/s  0.00 % 96.71 % php-fpm: pool ingatlan
 7099 be/4 ingatlan    0.00 B/s    0.00 B/s  0.00 % 94.44 % php-fpm: pool ingatlan
 7101 be/4 ingatlan    0.00 B/s    0.00 B/s  0.00 % 83.41 % php-fpm: pool ingatlan
 7577 be/4 ingatlan    0.00 B/s    0.00 B/s  0.00 % 77.91 % php-fpm: pool ingatlan
 6858 be/4 ingatlan    0.00 B/s    0.00 B/s  0.00 % 76.18 % php-fpm: pool ingatlan
 6831 be/4 ingatlan    0.00 B/s    0.00 B/s  0.00 % 75.55 % php-fpm: pool ingatlan
 1627 be/4 www-data 1050.01 K/s   13.55 K/s  0.00 % 28.58 % nginx: worker process
 7897 be/4 mysql       2.56 M/s   10.16 K/s  8.23 % 27.75 % mysqld --daemonize --pid-file=/run/mysqld/mysqld.pid
 1628 be/4 www-data 1178.72 K/s    3.39 K/s  0.00 % 22.60 % nginx: worker process
 6876 be/4 ingatlan    0.00 B/s    0.00 B/s  0.00 % 21.61 % php-fpm: pool ingatlan
 6964 be/4 ingatlan   64.36 K/s    0.00 B/s  0.00 % 21.04 % php-fpm: pool ingatlan
 7829 be/4 ingatlan  470.81 K/s    0.00 B/s  0.00 % 14.46 % php-fpm: pool ingatlan
 7104 be/4 ingatlan   88.07 K/s    0.00 B/s  0.00 %  4.95 % php-fpm: pool ingatlan
 7832 be/4 ingatlan   16.94 K/s    0.00 B/s  0.00 %  1.82 % php-fpm: pool ingatlan
 7228 be/4 ingatlan    3.39 K/s    0.00 B/s  0.00 %  1.19 % php-fpm: pool ingatlan
 7902 be/4 mysql       3.39 K/s    0.00 B/s  2.23 %  1.16 % mysqld --daemonize --pid-file=/run/mysqld/mysqld.pid
  329 be/3 root        0.00 B/s   13.55 K/s  0.00 %  0.07 % [jbd2/sda2-8]
 7116 be/4 ingatlan    0.00 B/s    3.39 K/s  0.00 %  0.00 % php-fpm: pool ingatlan
 7578 be/4 ingatlan    0.00 B/s   20.32 K/s  0.00 %  0.00 % php-fpm: pool ingatlan
 7770 be/4 mysql       3.39 K/s    0.00 B/s  4.24 %  0.00 % mysqld --daemonize --pid-file=/run/mysqld/mysqld.pid
 7907 be/4 mysql      10.16 K/s    0.00 B/s  1.48 %  0.00 % mysqld --daemonize --pid-file=/run/mysqld/mysqld.pid
    1 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % init
    2 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kthreadd]


```
Any idea on figuring out what might be going on with those processes?

Thanks!

---

### Post by slickymaster on 2018-08-27
*Thread moved to **Server Platforms**.*

---

### Post by Zolcsi on 2018-08-27
Well, I did lots of stuff, but it seems that MySQL was also clogging the disk.
Setting innodb_flush_method to O_DIRECT seems to have solved the issue.

---

