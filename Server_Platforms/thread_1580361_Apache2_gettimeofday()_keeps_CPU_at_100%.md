---
title: "Apache2 gettimeofday() keeps CPU at 100%"
date: 2010-09-23
forum: Server Platforms
---

### Post by RedLine on 2010-09-23
I use Ubuntu 6.06.2 LTS with Apache/2.0.55; built:Aug 16 2010 18:25:39 and PHP 5.1.2 (cli) (built: Sep 16 2010 20:32:18).

Apache processes load all the 4 cores to 100% and the systems accumulates load. When i strace -p apachepid i get only:
```
gettimeofday({1285245989, 960827}, NULL) = 0
gettimeofday({1285245989, 960880}, NULL) = 0
gettimeofday({1285245989, 960929}, NULL) = 0
gettimeofday({1285245989, 960966}, NULL) = 0
gettimeofday({1285245989, 961019}, NULL) = 0
gettimeofday({1285245989, 961067}, NULL) = 0
gettimeofday({1285245989, 961104}, NULL) = 0
gettimeofday({1285245989, 961157}, NULL) = 0
gettimeofday({1285245989, 961207}, NULL) = 0

```

Also the output of strace -fcp apache2 is:
```
% time     seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
100.00    0.003379           0    156119           gettimeofday
------ ----------- ----------- --------- --------- ----------------
100.00    0.003379                156119           total

```

Do you have any ideas?

UPDATED: The problem came from the WebApp that is running on the server. There was a bug that generated an infinite loop.

---

