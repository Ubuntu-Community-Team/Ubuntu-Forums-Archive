---
title: "Memory usage increasing - Who is the culprit?"
date: 2014-05-08
forum: Server Platforms
---

### Post by andrei-4 on 2014-05-08
On Ubuntu 14.04, Digital Ocean VPS, I run Apache, Tomcat, MySQL and Bind9. Nothing else (well, SSH, UFW, and some default services.).

Free memory drops by the minute.

After a restart top shows:
top - 01:40:14 up 1 min,  1 user,  load average: 0.15, 0.09, 0.04
Tasks:  73 total,   1 running,  72 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.3 us,  0.7 sy,  0.0 ni, 99.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:    501868 total,   298608 used,   **203260 free**,    19208 buffers
KiB Swap:        0 total,        0 used,        0 free.   137988 cached Mem


After 7 hours, 150MB of the 200MB free are used.
top - 01:32:55 up  6:59,  1 user,  load average: 0.00, 0.01, 0.05
Tasks:  73 total,   2 running,  71 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.3 sy,  0.0 ni, 99.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:    501868 total,   461944 used,    **39924 free**,    22696 buffers
KiB Swap:        0 total,        0 used,        0 free.   205900 cached Mem


How can I find the culprit?

Thanks,
Andrei

---

### Post by andrei-4 on 2014-05-08
**ps aux --sort -rss | head**
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
tomcat7   1227  3.9 28.8 933032 144880 ?       Sl   01:38   0:40 /usr/lib/jvm/java-7-oracle/bin/java (some content removed for clarity)... org.apache.catalina.startup.Bootstrap start
mysql     1049  0.1  9.3 550064 46876 ?        Ssl  01:38   0:01 /usr/sbin/mysqld
bind       963  0.0  2.7 164680 13956 ?        Ssl  01:38   0:00 /usr/sbin/named -u bind
www-data  1122  0.0  0.9 832760  4648 ?        Sl   01:38   0:00 /usr/sbin/apache2 -k start
www-data  1123  0.0  0.8 832744  4344 ?        Sl   01:38   0:00 /usr/sbin/apache2 -k start
root      1329  0.0  0.8 105628  4228 ?        Ss   01:39   0:00 sshd: root@pts/0
root      1378  0.0  0.6  22328  3432 pts/0    Ss   01:39   0:00 -bash
root      1120  0.0  0.6  76196  3252 ?        Ss   01:38   0:00 /usr/sbin/apache2 -k start
root       931  0.0  0.6  61364  3024 ?        Ss   01:38   0:00 /usr/sbin/sshd -D

**top**
top - 01:56:51 up 18 min,  1 user,  load average: 0.00, 0.05, 0.06
Tasks:  71 total,   1 running,  70 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.3 us,  0.3 sy,  0.0 ni, 99.3 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:    501868 total,   421868 used,    80000 free,    20204 buffers
KiB Swap:        0 total,        0 used,        0 free.   166832 cached Mem

---

### Post by sanderj on 2014-05-08
Does reading [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/) help you?

---

