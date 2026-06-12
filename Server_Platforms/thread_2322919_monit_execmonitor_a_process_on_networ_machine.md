---
title: "monit exec/monitor a process on networ machine"
date: 2016-05-01
forum: Server Platforms
---

### Post by YaPaY on 2016-05-01
Dear all,

for 2 days I am looking a solution for this. I installed monit on my server and I can get alerts but I need monitor processes on different machines and I have to start them from monit installed machine. I need monitor these process but problem is if any mumudvb process fail I have to start it with custom configuration file. Every single mumudvb process works with different config files. Is there any way to realize it monit?

Here is the quickview to processes:

```
[root@localhost ~]# ps aux | grep mumudvb
root      5034  4.8  0.6 103040 21116 ?        SLl  Apr29 175:13 mumudvb -d -c /root/42/12729
root      5691  6.1  0.6  37504 21108 ?        SLl  Apr29 221:56 mumudvb -d -c /root/42/12422
root      6160  3.1  0.6  37608 21080 ?        SLl  Apr29 114:26 mumudvb -d -c /root/42/12265
root      6796  7.6  0.6 103060 21136 ?        SLl  Apr29 275:19 mumudvb -d -c /root/42/10962
root      7209  7.2  0.6  37524 21128 ?        SLl  Apr29 263:44 mumudvb -d -c /root/42/11855
root      7774  6.6  0.6  37516 21120 ?        SLl  Apr29 241:36 mumudvb -d -c /root/42/11557
root      8154  8.4  0.6  37516 21120 ?        SLl  Apr29 304:43 mumudvb -d -c /root/42/11957
root     10964  5.6  0.6  37484 21088 ?        SLl  11:50  31:36 mumudvb -d -c /root/19/12544.75
root     13578  6.9  0.7  40092 23680 ?        SLl  10:10  45:38 mumudvb -d -c /root/13/12520
root     19671  0.0  0.0 112644   932 pts/12   R+   21:11   0:00 grep --color=auto mumudvb
root     24324  3.2  0.6 103040 21116 ?        SLl  Apr29 116:15 mumudvb -d -c /root/42/12525
root     27398  7.7  0.6  37508 21112 ?        SLl  10:25  50:11 mumudvb -d -c /root/19/12187.50
root     32246  3.3  0.6 103124 21200 ?        SLl  Apr29 110:28 mumudvb -d -c /root/42/11096 -v --card7

```

---

### Post by DuckHook on 2016-05-01
*Your thread has been moved to **Server Platforms** as the forum more suited to your issue.*

---

