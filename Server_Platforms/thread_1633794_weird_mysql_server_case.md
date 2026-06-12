---
title: "weird mysql server case"
date: 2010-11-29
forum: Server Platforms
---

### Post by smo0th on 2010-11-29
Suddenly, the server went overloaded to a load higher than 110, it has 8 cores and 68 GB of RAM, it's actually running 6 databases using mysql_multi and they are configured to use a maximum of 64 GB, so I'm just wondering what happened.. it's a dedicated server only for mysql.

I have already checked all system logs and also some munin graphs, from these munin graphs, at the time, memory and CPU seemed fine, munin polls for data every 5 min so something nasty happened in a short amount of time, disk space was fine(I saw the load right before it went non responsive).

I'm just trying to find out what happened that caused the load to skyrocket like that and caused the server to be non responsive, what else could I do?

Any help would be appreciated,

---

### Post by smo0th on 2010-12-09
no ideas out there?

---

### Post by kbubunt on 2010-12-09
What sort of strain was it under at the time?

---

### Post by smo0th on 2010-12-10
well, I guess around 4000 users were working a t the same time that day, but that happens every day, since logs are useless on this case I just want to check any ideas you may have out there, I guess at this point finding a root cause is virtually impossible

---

