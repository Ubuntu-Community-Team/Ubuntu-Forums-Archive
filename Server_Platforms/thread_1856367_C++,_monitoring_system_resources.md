---
title: "C++, monitoring system resources"
date: 2011-10-08
forum: Server Platforms
---

### Post by bbqroast on 2011-10-08
Does anyone know a good guide on (efficiently) accessing variables such as CPU and RAM usage in Ubuntu??
I am using C++ and want to kind of fix this with as little extra software as possible (after all a empty server is a safe server).

---

### Post by Jonathan L on 2011-10-09
> **bbqroast said:**
> Does anyone know a good guide on (efficiently) accessing variables such as CPU and RAM usage in Ubuntu??
I am using C++ and want to kind of fix this with as little extra software as possible (after all a empty server is a safe server).

Hi BBQ

You can read the proc filesystem which has many useful (virtual) files see manual for proc(5)
```
cat /proc/loadavg
cat /proc/meminfo
```Another possibilty would be to use exec an appropriate sysctl( 8 ) command.  Or finally you could use the depreceated sysctl(2) interface.

Hope that helps.
Jonathan.

---

