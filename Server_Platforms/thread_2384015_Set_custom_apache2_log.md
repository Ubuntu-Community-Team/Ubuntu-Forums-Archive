---
title: "Set custom apache2 log"
date: 2018-02-01
forum: Server Platforms
---

### Post by dam034 on 2018-02-01
Dear users,

actually I have apache2 with default log, because I don't know how to edit the log setting.

I listed the apache2 log folder:
```
root@vps1238:/var/log/apache2# ls -ahl
totale 140K
drwxr-x---  2 root adm    4,0K feb  1 06:25 .
drwxrwxr-x 12 root syslog 4,0K feb  1 06:25 ..
-rw-r-----  1 root adm    2,6K feb  1 14:44 access.log
-rw-r-----  1 root adm    8,6K feb  1 05:50 access.log.1
-rw-r-----  1 root adm     683 gen 23 05:30 access.log.10.gz
-rw-r-----  1 root adm    2,4K gen 22 02:32 access.log.11.gz
-rw-r-----  1 root adm    1,3K gen 21 05:29 access.log.12.gz
-rw-r-----  1 root adm    1,1K gen 20 05:09 access.log.13.gz
-rw-r-----  1 root adm     492 gen 19 03:56 access.log.14.gz
-rw-r-----  1 root adm     793 gen 31 05:11 access.log.2.gz
-rw-r-----  1 root adm     563 gen 30 05:22 access.log.3.gz
-rw-r-----  1 root adm    1,1K gen 29 03:23 access.log.4.gz
-rw-r-----  1 root adm    1,3K gen 28 02:40 access.log.5.gz
-rw-r-----  1 root adm    1019 gen 27 05:29 access.log.6.gz
-rw-r-----  1 root adm     960 gen 26 06:11 access.log.7.gz
-rw-r-----  1 root adm     981 gen 25 04:41 access.log.8.gz
-rw-r-----  1 root adm     735 gen 24 06:16 access.log.9.gz
-rw-r-----  1 root adm    1,5K feb  1 13:28 error.log
-rw-r-----  1 root adm    7,1K feb  1 06:25 error.log.1
-rw-r-----  1 root adm     887 gen 23 06:25 error.log.10.gz
-rw-r-----  1 root adm     850 gen 22 06:25 error.log.11.gz
-rw-r-----  1 root adm    1,5K gen 21 06:25 error.log.12.gz
-rw-r-----  1 root adm    1,4K gen 20 06:25 error.log.13.gz
-rw-r-----  1 root adm     954 gen 19 06:25 error.log.14.gz
-rw-r-----  1 root adm    1,1K gen 31 06:25 error.log.2.gz
-rw-r-----  1 root adm     806 gen 30 06:25 error.log.3.gz
-rw-r-----  1 root adm    1,3K gen 29 06:25 error.log.4.gz
-rw-r-----  1 root adm    1,3K gen 28 06:25 error.log.5.gz
-rw-r-----  1 root adm    1,2K gen 27 06:25 error.log.6.gz
-rw-r-----  1 root adm    1,1K gen 26 06:25 error.log.7.gz
-rw-r-----  1 root adm    1002 gen 25 06:25 error.log.8.gz
-rw-r-----  1 root adm    1,2K gen 24 06:25 error.log.9.gz
-rw-r-----  1 root adm       0 dic 10 16:37 other_vhosts_access.log

```

Now I want:
[LIST]
[*]none compression of log file (e.g. gz)
[*]a log file for a small size (es. 1MB)
[*]to log only some informations, such as ip, request, date, response code, response length
[/LIST]

I know I have to edit /etc/apache2/apache2.conf

Please advice!

---

