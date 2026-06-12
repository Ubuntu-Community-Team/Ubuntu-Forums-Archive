---
title: "oom-killer control"
date: 2010-07-05
forum: Server Platforms
---

### Post by johndunne on 2010-07-05
Hi,

I'm looking to disable oom-killer on ubuntu 10.04. I'm actually trying to investigate an issue where oom-killer is invoked by my application when there is still over 1GB (of 2GB total) of free ram still available, according to meminfo.

Typcically, 

     echo "0" > /proc/sys/vm/oom-kill

is enough to disable oom-killer on other linux platforms but not on my Ubuntu 10.04. How is oom-killer disabled on Ubuntu?

---

### Post by sjinks on 2010-07-05
I would say you need to 

echo 2 > /proc/sys/vm/overcommit_memory
echo 100 > /proc/sys/vm/overcommit_ratio

The first one will disable overcommit, the second will set overcommit ratio to 100%. See proc(5) for details.

---

### Post by johndunne on 2010-07-06
Hi sjinks,

Thanks for your suggestion. I've applied those values but oom killer is still invoked. Very strange as the system appears to be running normal and then predicatably and repeatably crashes at nearly the same point during testing. My understanding is that oom killer is only invoked when memory is critically low - however there is plenty of free RAM available at the point when oom killer is called. I'm thinking oom killer isn't behaving itself or perhaps my understanding isnt yet complete enough. I'm continuing to investigate!

---

### Post by sjinks on 2010-07-06
Hi John,

Are you sure this is OOM killer? Do you see "out of memory" messages in /var/log/syslog or /var/log/kern.log?

---

### Post by sjinks on 2010-07-06
As a last resort you can execute this from your /etc/rc.local:

for i in /proc/*/oom_adj; do echo "-17" > $i; done

This will disable OOM killer for all processes. Since new processes inherit their parents' oom_adj setting, all new processes will have OOM killer disabled for them as well.

---

### Post by Innate Ideas on 2010-10-20
If you are running the 32bit kernel your problem may be that you are running out of memory below 1024k which the 32bit kernel uses to manage memory. I encountered this problem on a box with 32GB of memory, the box had gigs of memory free but oom-killer was killing processes and the box would crash. See this link for a description of my problem, and solution:  [http://www.innate-ideas.net/2010/05/out-of-memory-killer.html](http://www.innate-ideas.net/2010/05/out-of-memory-killer.html)

---

