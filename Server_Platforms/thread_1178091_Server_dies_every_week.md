---
title: "Server dies every week"
date: 2009-06-04
forum: Server Platforms
---

### Post by brack on 2009-06-04
My VPS dies every week and support team cannot find a reason. 
I have Ubuntu 8.04 server on 256mb RAM and 25Gb HDD Running one typo3 site on it. Managed by Virtualmin/Webmin The last die was yesterday and here is the portion of syslog where actuall out_of_memory event makes server die:
```
Jun  3 13:13:37 ywamrest postfix/qmgr[1388]: DB5F12241B5: from=<xxxxxxx@xxxxxxxxxx.org>, size=75407, nrcpt=1 (queue active)
Jun  3 13:28:07 ywamrest /USR/SBIN/CRON[752]: (root) CMD (/etc/webmin/status/monitor.pl)
Jun  3 13:28:12 ywamrest /USR/SBIN/CRON[755]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun  3 13:29:51 ywamrest kernel: apache2 invoked oom-killer: gfp_mask=0x201d2, order=0, oomkilladj=0
Jun  3 13:45:03 ywamrest /USR/SBIN/CRON[770]: (root) CMD (/etc/webmin/status/monitor.pl)
Jun  3 13:58:18 ywamrest kernel: 
Jun  3 14:00:36 ywamrest /USR/SBIN/CRON[783]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Jun  3 14:02:36 ywamrest mysqld_safe[781]: Number of processes running now: 0
Jun  3 14:03:35 ywamrest kernel: Call Trace:
Jun  3 14:16:47 ywamrest kernel:  [<ffffffff802bb6a0>] out_of_memory+0x8b/0x203
Jun  3 14:20:03 ywamrest mysqld_safe[838]: restarted
Jun  3 14:24:58 ywamrest /USR/SBIN/CRON[855]: (root) CMD (/etc/webmin/status/monitor.pl)
Jun  3 14:26:22 ywamrest /USR/SBIN/CRON[858]: (root) CMD (/etc/webmin/status/monitor.pl)
Jun  3 14:27:46 ywamrest /USR/SBIN/CRON[860]: (root) CMD (/home/restenas/domains/ywamrestenas.se/public_html/typo3conf/ext/tcdirectmail/mailer.php)
Jun  3 14:29:43 ywamrest postfix/smtpd[739]: warning: connect #1 to subsystem private/proxymap: Connection refused

```

---

### Post by AndyCee on 2009-06-04
I generally avoid giving suggestions to people using server editions, but is it entirely possible that your server doesn't have enough memory?

I know 256MB is the minimum requirement to install ubuntu server, but if you are getting an out_of_memory error, and you're running the minimum just for *installation*, couldn't that be what's happening?

---

### Post by brack on 2009-06-04
> **AndyCee said:**
> I generally avoid giving suggestions to people using server editions, but is it entirely possible that your server doesn't have enough memory?

I know 256MB is the minimum requirement to install ubuntu server, but if you are getting an out_of_memory error, and you're running the minimum just for *installation*, couldn't that be what's happening?

according to here: [https://help.ubuntu.com/8.04/serverguide/C/preparing-to-install.html](https://help.ubuntu.com/8.04/serverguide/C/preparing-to-install.html) minimum requirement for Ubuntu 8.04 server is 128Mb And I was trying to shave the server as much as possible, in normal circumstances this server uses only 170Mb of memory, but once a week... almost at the same time it goes out of memory. I dont know how to debug the problem, I'm too new to all this stuff.

---

### Post by skymera on 2009-06-04
Do you have a swap partition?

If not, create one. Some memory can be transferred from RAM to swap so hpefully no more out of memory errors

---

### Post by leandromartinez98 on 2009-06-04
Anyway I wouldn't expect the server to die because of that. Have you
run a memory test to see if there is no hardware memory problems?
Another common reason for a machine to die is overheating, many
times caused by simple issues as a malfunctioning fan or old
conducting paste in the processor heat sink.

---

### Post by iponeverything on 2009-06-04
Something on your system has a memory leak.

An easy way to debug it would be have cron email you the output of 
the below command every hour.

```
ps uaxwwww | sort -g -k 6 | tail -5
```

---

### Post by brack on 2009-06-04
> **skymera said:**
> Do you have a swap partition?

If not, create one. Some memory can be transferred from RAM to swap so hpefully no more out of memory errors

Yes, there is swap partition 390Mb 

And I run memory test everything is ok, but I dont know if it is the possibility because this is NOT a dedicated server, it is Virtual private server. I agree that memory is not much but it should work fine on 256Mb When I reboot vps and then all week long it keeps only around 170Mb, the rest is free. Then the CPU activity raises up to 100% and vps dies. Support team sincerely tried to help and the support ticket is still active but site is still falling down regularly. There where a few things that I've changed since fresh installation and one of them was enabling InnoDB engine. So, I'm thinking maybe this could lead to regular failings? How to configure innoDB for small amount of memory and how to debug it? There are no errors in mysql.log

---

### Post by brack on 2009-06-04
> **iponeverything said:**
> Something on your system has a memory leak.

An easy way to debug it would be have cron email you the output of 
the below command every hour.

```
ps uaxwwww | sort -g -k 6 | tail -5
```

How can I read this output? what are those things mean and what should I consider the "bad signs"

---

### Post by brack on 2009-06-04
Ok I put "0 * * * * ps uaxwwww | sort -g -k 6 | tail -5 > /var/log/ps.log" into crontab and will wait now for the bad process to be revealed.

---

### Post by leandromartinez98 on 2009-06-04
> **brack said:**
> Ok I put "0 * * * * ps uaxwwww | sort -g -k 6 | tail -5 > /var/log/ps.log" into crontab and will wait now for the bad process to be revealed.


I suggest also putting:

top -n 1 b > /var/log/top.log

in crontab, because this will give the information on what is the process
that is consuming your cpu (if you don't know yet). I had some problems
with a server once, and the cpu was being consumed by some system tools
that were actually trying to warn me that the cpu was overheating.

---

### Post by brack on 2009-06-04
> **leandromartinez98 said:**
> I suggest also putting:

top -n 1 b > /var/log/top.log

Ok, done. But how could overheat influence Virtual server?

---

### Post by iponeverything on 2009-06-04
> **brack said:**
> How can I read this output? what are those things mean and what should I consider the "bad signs"

The fields are:

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
```

Fields 4, 5, 6 and 11 are the ones you want to keep an eye on.

---

### Post by leandromartinez98 on 2009-06-04
> **brack said:**
> Ok, done. But how could overheat influence Virtual server?

I'm sorry, I missed the Virtual part, I thought that the machine
was going down.

---

### Post by iponeverything on 2009-06-04
> **brack said:**
> Ok I put "0 * * * * ps uaxwwww | sort -g -k 6 | tail -5 > /var/log/ps.log" into crontab and will wait now for the bad process to be revealed.

You do realize that unless you use ">>" instead of ">" your log is going to get overwritten every time cron runs. 

you might try something like:


```
0 * * * *  echo `date` >> /var/log/ps.log; echo ================= >> /var/log/ps.log; ps uaxwwww | sort -g -k 6 | tail -5 >> /var/log/ps.log 
```

to make it easier to read.

---

### Post by brack on 2009-06-25
Ok, here I'm back with the results of tracing the server for over two weeks. There where two downs at the server. During the first one I didnt notice too much of changes except there were couple of more apache2 services running but look at the top of second down time:
```
top - 11:21:36 up 11 days, 33 min,  1 user,  load average: 86.61, 87.19, 82.34
Tasks: 167 total,   1 running, 166 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.5%us,  0.5%sy,  0.0%ni, 94.8%id,  3.0%wa,  0.0%hi,  0.0%si,  0.2%st
Mem:    262144k total,   257648k used,     4496k free,      268k buffers
Swap:   393208k total,   393004k used,      204k free,     7532k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
31210 restenas  18   0 47028 8228   32 D    0  3.1   0:40.54 apache2           
31246 restenas  18   0 37604 3532   16 D    0  1.3   0:40.10 apache2           
31323 restenas  18   0 32188 1004   68 D    0  0.4   0:09.68 apache2           
31232 restenas  18   0 43036 4588   32 D    0  1.8   0:31.43 apache2           
31195 restenas  18   0 63736 9304   32 D    0  3.5   0:40.43 apache2           
31266 root      18   0 13480  176   16 D    0  0.1   0:30.03 mailer.php         
31301 root      18   0  5020  272   80 D    0  0.1   0:24.04 sshd               
31342 root      18   0  4572  160   40 D    0  0.1   0:00.93 mail               
31345 root      18   0  2344  228  108 D    0  0.1   0:00.25 cron               
1053 syslog    18   0  1872  132   56 D    0  0.1   0:25.48 syslogd           
31003 restenas  18   0 62152 8784   32 D    0  3.4   0:44.94 apache2           
31293 restenas  18   0 32848 1560   52 D    0  0.6   0:27.34 apache2           
31305 restenas  18   0 32320 1040   28 D    0  0.4   0:12.81 apache2           
31335 root      16   0  2240  460  180 R    0  0.2   0:01.47 top               
31236 restenas  18   0 32668 1644   32 D    0  0.6   0:37.59 apache2           
1625 root      18   0 11036  464   56 D    0  0.2   0:38.84 miniserv.pl       
31334 root      18   0  2372  212   64 D    0  0.1   0:02.13 cron               
31234 restenas  18   0 24504 1352   36 D    0  0.5   0:38.11 apache2           
31304 restenas  18   0 32188 1076   80 D    0  0.4   0:13.03 apache2           
31298 root      18   0  5424  252   76 D    0  0.1   0:25.56 smtpd             
31277 restenas  18   0 33952 2012   28 D    0  0.8   0:34.08 apache2           
31260 restenas  18   0 37092 3000   24 D    0  1.1   0:29.59 apache2           
31286 root      18   0  5256  300   68 D    0  0.1   0:32.00 sshd               
31292 restenas  18   0 34788 2540   48 D    0  1.0   0:28.46 apache2           
31127 restenas  18   0 59180 2692   40 D    0  1.0   0:39.44 apache2           
31129 restenas  18   0 56708 2844   20 D    0  1.1   0:41.79 apache2           
31250 restenas  18   0 33960 1980   28 D    0  0.8   0:39.24 apache2           
31328 root      18   0  4636  336   84 D    0  0.1   0:04.36 collectinfo.pl     
31331 root      18   0  4632  404  160 D    0  0.2   0:03.98 monitor.pl         
1370 postfix   18   0  5500  136   24 D    0  0.1   0:33.83 qmgr               
1612 bind      25   0 54164  392   48 S    0  0.1   1:15.76 named             
31198 restenas  18   0 64236 9320   32 D    0  3.6   0:42.82 apache2           
31209 restenas  18   0 24504 1536   64 D    0  0.6   0:39.26 apache2           
31242 restenas  18   0 32676 1688   32 D    0  0.6   0:38.32 apache2           
31267 restenas  18   0 34788 2392  100 D    0  0.9   0:31.31 apache2           
31290 root      18   0 10528   96   40 D    0  0.0   0:30.42 mysqld             
2224 root      18   0  2248  544  332 D    0  0.2   3:31.45 top               
31083 postfix   18   0  5336   88   16 D    0  0.0   0:35.96 pickup             
31193 restenas  18   0 45172 4620   20 D    0  1.8   0:37.91 apache2           
31208 restenas  18   0 47620 4456    4 D    0  1.7   0:29.28 apache2           
31212 restenas  18   0 45740 9484   32 D    0  3.6   0:40.36 apache2           
31220 restenas  18   0 47568 8360   32 D    0  3.2   0:40.55 apache2           
31279 restenas  18   0 32848 1548   44 D    0  0.6   0:33.00 apache2           
31348 root      18   0  1676   68    4 D    0  0.0   0:00.10 sed               
31235 restenas  18   0 32668 1684   40 D    0  0.6   0:36.69 apache2           
31263 restenas  18   0 37604 4420   32 D    0  1.7   0:32.74 apache2           
31218 restenas  18   0 50132 8264   32 D    0  3.2   0:43.54 apache2           
31228 restenas  18   0 42512 4624   16 D    0  1.8   0:32.63 apache2           
31336 root      18   0  4572  160   40 D    0  0.1   0:01.93 mail               
31347 root      18   0  1700   64    4 S    0  0.0   0:00.07 maxlifetime       
31211 restenas  18   0 47028 8884   32 D    0  3.4   0:40.55 apache2           
31247 restenas  18   0 36324 2752   20 D    0  1.0   0:37.91 apache2           
31249 restenas  18   0 37604 3180   84 D    0  1.2   0:35.98 apache2           
31264 restenas  18   0 34788 2320   56 D    0  0.9   0:32.02 apache2           
31281 root      18   0  7380  228   36 D    0  0.1   0:31.51 mail               
31300 restenas  18   0 32848 1648   56 D    0  0.6   0:27.42 apache2           
31344 root      18   0  7980  156   32 D    0  0.1   0:00.71 mailer.php         
31159 restenas  18   0 40220 2860   32 D    0  1.1   0:34.66 apache2           
31219 restenas  18   0 38212 3944   28 D    0  1.5   0:34.51 apache2           
31269 restenas  18   0 34796 2404   48 D    0  0.9   0:32.72 apache2           
31316 root      18   0 12788  204   60 D    0  0.1   0:07.65 mailer.php         
   96 root      10  -5     0    0    0 S    0  0.0   2:38.34 kswapd0           
31207 root      18   0 14984 1740  108 D    0  0.7   0:35.53 miniserv.pl       
31215 restenas  18   0 47052 8880   28 D    0  3.4   0:40.32 apache2           
31227 restenas  18   0 43536 4144   40 D    0  1.6   0:29.89 apache2           
31262 restenas  18   0 37604 3536   16 D    0  1.3   0:31.32 apache2           
31273 restenas  18   0 34788 2304   24 D    0  0.9   0:29.22 apache2           
31299 restenas  18   0 32848 1596   56 D    0  0.6   0:29.08 apache2           
31125 restenas  18   0 42592 7048  200 D    0  2.7   0:42.55 apache2           
31280 root      18   0  7376  224   32 D    0  0.1   0:31.01 mail               
1463 root      18   0 31792  676   60 S    0  0.3   0:31.17 apache2           
31163 restenas  18   0 64232 9.9m   32 D    0  3.9   0:43.49 apache2           
1426 proftpd   16   0  9892   92    4 S    0  0.0   0:30.02 proftpd           
31226 restenas  18   0 27196 1548   24 D    0  0.6   0:38.61 apache2           
31268 restenas  18   0 34788 2380   56 D    0  0.9   0:30.82 apache2           
31339 root      18   0  2584  376  228 D    0  0.1   0:01.74 ps                 
    1 root      15   0  2772    8    4 S    0  0.0   0:01.05 init               
    2 root      RT  -5     0    0    0 S    0  0.0   0:42.05 migration/0       
    3 root      34  19     0    0    0 S    0  0.0   0:00.31 ksoftirqd/0       
    4 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S    0  0.0   0:00.01 events/0           
    6 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper           
    7 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthread           
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 xenwatch           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 xenbus             
   15 root      RT  -5     0    0    0 S    0  0.0   0:10.69 migration/1       
   16 root      34  19     0    0    0 S    0  0.0   0:00.11 ksoftirqd/1       
   17 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
   18 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   21 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0         
   22 root      10  -5     0    0    0 S    0  0.0   0:00.03 kblockd/1         
   23 root      20  -5     0    0    0 S    0  0.0   0:00.00 cqueue/0           
   24 root      10  -5     0    0    0 S    0  0.0   0:00.00 cqueue/1           
   28 root      20  -5     0    0    0 S    0  0.0   0:00.00 khubd             
   30 root      10  -5     0    0    0 S    0  0.0   0:00.00 kseriod           
   97 root      20  -5     0    0    0 S    0  0.0   0:00.00 aio/0             
   98 root      20  -5     0    0    0 S    0  0.0   0:00.00 aio/1             
  228 root      11  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused         
  259 root      16  -5     0    0    0 S    0  0.0   0:00.00 ata/0             
  260 root      16  -5     0    0    0 S    0  0.0   0:00.00 ata/1             
  261 root      16  -5     0    0    0 S    0  0.0   0:00.00 ata_aux           
  271 root      10  -5     0    0    0 D    0  0.0   0:11.35 kjournald         
  390 root      20  -4  2156    8    4 S    0  0.0   0:00.03 udevd             
1001 root      16   0  1644    8    4 S    0  0.0   0:00.00 getty             
1002 root      16   0  1640    8    4 S    0  0.0   0:00.00 getty             
1004 root      18   0  1644    4    4 S    0  0.0   0:00.00 getty             
1006 root      18   0  1644    4    4 S    0  0.0   0:00.00 getty             
1007 root      18   0  1640    4    4 S    0  0.0   0:00.00 getty             
1074 root      18   0  1800   12    4 S    0  0.0   0:00.26 dd                 
1076 klog      16   0  2256   56    4 S    0  0.0   0:01.24 klogd             
1126 root      16   0  5252   52    4 S    0  0.0   0:01.98 sshd               
1184 root      16   0  1700    8    4 S    0  0.0   0:00.00 mysqld_safe       
1362 root      15   0  5328   72    4 S    0  0.0   0:09.28 master             
1391 root      20   0  6872    4    4 S    0  0.0   0:00.00 saslauthd         
1392 root      18   0  6872    4    4 S    0  0.0   0:00.00 saslauthd         
1393 root      18   0  6872    4    4 S    0  0.0   0:00.00 saslauthd         
1394 root      20   0  6872    4    4 S    0  0.0   0:00.00 saslauthd         
1395 root      20   0  6872    4    4 S    0  0.0   0:00.00 saslauthd         
1442 root      18   0  2044   68    4 S    0  0.0   0:32.28 cron               
1477 root      18   0 31552    4    4 S    0  0.0   0:02.53 lookup-domain-d   
1525 root      18   0  9812  540   88 D    0  0.2   0:42.90 miniserv.pl       
1551 root      15   0  2944    4    4 S    0  0.0   0:00.00 login             
1565 root      16   0  4092    4    4 S    0  0.0   0:00.00 bash               
5167 postfix   16   0  6008  136   36 D    0  0.1   0:03.00 tlsmgr             
7578 restenas  17   0 21476  296    4 S    0  0.1   0:00.00 apache2           
7579 restenas  18   0 21796  416   68 D    0  0.2   0:32.59 apache2           
13439 root      15   0     0    0    0 S    0  0.0   0:00.47 pdflush           
31185 restenas  18   0 45172 4932   28 D    0  1.9   0:34.14 apache2           
31192 root      18   0 34876 1828   76 D    0  0.7   0:41.13 miniserv.pl       
31194 restenas  18   0 64244 9152   24 D    0  3.5   0:41.03 apache2           
31206 restenas  18   0 39944 3856  100 D    0  1.5   0:34.94 apache2           
31217 restenas  18   0 50648 6168   16 D    0  2.4   0:39.28 apache2           
31237 restenas  18   0 32668 1356   28 D    0  0.5   0:40.30 apache2           
31252 root      18   0  2380   24    4 S    0  0.0   0:04.27 cron               
31253 root      18   0  2380   32    4 S    0  0.0   0:04.48 cron               
31254 root      18   0  2380   40    4 S    0  0.0   0:03.45 cron               
31261 restenas  18   0 36324 3416   16 D    0  1.3   0:32.40 apache2           
31265 root      18   0  1700   16    4 S    0  0.0   0:00.00 sh                 
31270 root      15   0  1696   20    4 S    0  0.0   0:00.00 sh                 
31271 root      18   0  1700   20    4 S    0  0.0   0:00.00 sh                 
31291 root      18   0  1624   20    4 S    0  0.0   0:00.00 logger             
31294 root      15   0     0    0    0 S    0  0.0   0:00.31 pdflush           
31296 root      18   0  2380   56    4 S    0  0.0   0:13.57 cron               
31302 root      18   0  2380   52    4 S    0  0.0   0:09.46 cron               
31303 restenas  18   0 32320 1080  136 D    0  0.4   0:13.61 apache2           
31307 root      18   0  1696   40    4 S    0  0.0   0:00.24 sh                 
31309 root      18   0  1696   24    4 S    0  0.0   0:00.20 sh                 
31310 root      18   0  1700   64    4 S    0  0.0   0:05.24 maxlifetime       
31311 root      18   0  3008   44    4 S    0  0.0   0:05.63 xargs             
31312 root      18   0  2380   68    4 S    0  0.0   0:05.38 cron               
31313 root      18   0  2380   96    4 S    0  0.0   0:04.62 cron               
31314 root      18   0  1696   32    4 S    0  0.0   0:00.00 sh                 
31320 root      18   0  2380  116    4 S    0  0.0   0:04.56 cron               
31321 root      18   0  2380  100    4 S    0  0.0   0:04.08 cron               
31322 root      18   0  2380  124    4 S    0  0.0   0:03.08 cron               
31324 root      18   0  1696   56    4 S    0  0.0   0:01.86 sh                 
31325 root      18   0  1696   40    4 S    0  0.0   0:01.82 sh                 
31326 root      18   0  2376  148    4 D    0  0.1   0:04.20 cron               
31327 root      18   0  2376  148    4 D    0  0.1   0:03.78 cron               
31329 root      18   0  1696   68    4 S    0  0.0   0:01.21 sh                 
31330 root      18   0  1692   60    4 S    0  0.0   0:00.73 sh                 
31333 root      18   0  1696   72    4 S    0  0.0   0:00.59 sh                 
31340 root      18   0 12268  112    4 S    0  0.0   0:00.62 sort               
31341 root      18   0  3016  104    4 S    0  0.0   0:00.28 tail               
31343 root      18   0  2368  340  204 D    0  0.1   0:00.80 cron               
31346 root      18   0  2376  148    4 S    0  0.1   0:00.00 cron               
31349 root      18   0  2376  148    4 S    0  0.1   0:00.00 cron 
```   

And here is the ps:
```
restenas 31215  1.4  2.8  42172  7488 ?        D    10:24   0:08 /usr/sbin/apache2 -k start
restenas 31211  1.3  3.0  43940  8124 ?        D    10:23   0:08 /usr/sbin/apache2 -k start
restenas 31220  1.4  4.3  46800 11364 ?        D    10:24   0:08 /usr/sbin/apache2 -k start
restenas 31217  1.4  4.5  48340 12024 ?        D    10:24   0:08 /usr/sbin/apache2 -k start
restenas 31218  1.5  4.9  50648 13068 ?        D    10:24   0:08 /usr/sbin/apache2 -k start
```

I set apache2 Maximum spare server processes to 2 and Initial server processes also 2 and Minimum spare server processes is also 2 and you can see how many apache2 running above. So, apache2 is the service that gives trouble once a week.

Would be very grateful for solution.

---

