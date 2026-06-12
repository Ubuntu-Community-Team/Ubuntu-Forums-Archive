---
title: "How can i list the load average per core not just the average for all cores"
date: 2010-12-21
forum: Server Platforms
---

### Post by jbencic on 2010-12-21
How can i find the load average per core?

i believe that the load average from 'uptime' is an average of all cores/cpu's on a system

[http://blog.scoutapp.com/articles/2009/07/31/understanding-load-averages]("http://blog.scoutapp.com/articles/2009/07/31/understanding-load-averages")

from a monitoring perspective if i have a load average of 3 on a 8 way box that may not be an issue as from the link above the load is is multiplied by the number of cores/cpu's so a load of 8 can mean there is not processes waiting for cpu time.

one issue could be that one processor/core may have a load of 3 and the rest < 1, this would indicate a rouge process. 

mpstat -P ALL  lists all processes,  how can I convert the output columns ( %user %nice %sys %iowait %irq %soft %steal %idle) to load 

the command 'sar' does another good job but need to convert the columns as well

in the end i want to find out if a core has a rouge process that needs to be killed.

---

### Post by stmiller on 2010-12-21
> **jbencic said:**
> 
one issue could be that one processor/core may have a load of 3 and the rest < 1, this would indicate a rouge process. 


Maybe. But maybe that process or program is only single threaded. Then it would just ramp up one cpu and effect the 'load' per cpu. Or take rsync which seems to only use max two CPUs no matter how many cores you have, etc.

I wouldn't worry about it. Check out atop, htop, vmstat, (and related iftop) which are cool for monitoring your system for what you are after.

---

