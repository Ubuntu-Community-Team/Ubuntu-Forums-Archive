---
title: "MRTG is running but not updating the png graph"
date: 2015-01-20
forum: Server Platforms
---

### Post by raphael8 on 2015-01-20
Hi everyone,

I wanted to install mrtg to monitor the load on a server, I did that many times long time ago, but this time with surprise mrtg is working, no errors but not updating my graphs.
It's currently running and updating my files and logs.

The mem graphs are updated normally.

If you guys have a clue for me that would be appreciated.
Thanks a lot
Raphael



> 
root@meh:/var/www/mrtg# ls -ltr
total 256
-rwxrwxr-- 1 root root  1759 Jan 20 14:17 mrtg-r.png
-rwxrwxr-- 1 root root   414 Jan 20 14:17 mrtg-m.png
-rwxrwxr-- 1 root root   538 Jan 20 14:17 mrtg-l.png
-rw-r--r-- 1 root root  1358 Jan 20 18:58 system-load-week.png
-rw-r--r-- 1 root root  1297 Jan 20 18:58 system-load-month.png
-rw-r--r-- 1 root root  1701 Jan 20 18:58 system-load-year.png
-rwxrwxr-- 1 root root  2649 Jan 20 19:08 index.html
-rw-r--r-- 1 root root  1409 Jan 20 19:09 mem-week.png
-rw-r--r-- 1 root root  1750 Jan 20 19:09 mem-year.png
-rw-r--r-- 1 root root  1331 Jan 20 19:09 mem-month.png
-rw-r--r-- 1 root root  48182 Jan 20 19:19 system-load.old
-rw-r--r-- 1 root root  48208 Jan 20 19:19 mem.old
-rw-r--r-- 1 root root  48182 Jan 20 19:24 system-load.log
-rw-r--r-- 1 root root  1383 Jan 20 19:24 system-load-day.png
-rw-r--r-- 1 root root  6054 Jan 20 19:24 system-load.html
-rw-r--r-- 1 root root  48243 Jan 20 19:24 mem.log
-rw-r--r-- 1 root root  1437 Jan 20 19:24 mem-day.png
-rw-r--r-- 1 root root  5349 Jan 20 19:24 mem.html
root@meh:/var/www/mrtg#


> 
WorkDir: /var/www/mrtg
EnableIPv6: no


RunAsDaemon: Yes
Interval: 5


Target[system-load]: `/usr/bin/mrtg-load -m 200`
Title[system-load]: System Load
PageTop[system-load]: <H1>System Load</H1>
MaxBytes[system-load]: 200
Options[system-load]: unknaszero gauge
ShortLegend[system-load]:
YLegend[system-load]: 200x Load


Target[mem]: `bash /etc/mrtg/mem.sh`
Options[mem]: nopercent,gauge,noinfo, nobanner
Unscaled[mem]:dwmy
MaxBytes[mem]: 3630060000
Kilo[mem]:1024
YLegend[mem]: RAM
ShortLegend[mem]: o
Legend1[mem]: Memory free
Legend2[mem]: Memory used
LegendI[mem]: Memory free:
LegendO[mem]: Memory used:
Title[mem]: Memory
PageTop[mem]: <h1>Memory</h1>
WithPeak[mem]:wmy
Legend3[mem]: Memory free max
Legend4[mem]: Memory used max


---

### Post by SeijiSensei on 2015-01-20
Do you have the correct permissions on the directory where the graphs are stored?  Can the mrtg program write to them, and the web server read them?

---

### Post by raphael8 on 2015-01-20
Yes all is good, the memory graph actually works.

---

