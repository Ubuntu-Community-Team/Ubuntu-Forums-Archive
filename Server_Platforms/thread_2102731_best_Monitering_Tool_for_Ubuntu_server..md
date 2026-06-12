---
title: "best Monitering Tool for Ubuntu server."
date: 2013-01-08
forum: Server Platforms
---

### Post by ketan985 on 2013-01-08
I have deployed Ubuntu servers on my remote site and I need to monitor following parameters of my servers.

CPU usage, memory, load average, top memory and cpu  consuming processes list, 

I want to make that If any server goes down , I can check actual process behind that so I need list  of top ten CPU usage processes. 

Currently I am using Cacti server but I only miss top memory and cpu consuming process list. I am looking for best monitoring tool that provide such functionality.

---

### Post by spynappels on 2013-01-08
I don't think there is a single solution which will do exactly what you want. 

For total system RAM, swap and CPU usage, sar (from the sysstat package) can collect this data at 5 minute intervals and store up to a month's worth of data. It does not tell you which service consumed each though.

For granular data collection, you could tweak a ```
ps -efo comm,pid,ppid,rss,vsz
``` command to give you the info you need and run it from a cron job at whatever interval you want. Man pages are your friend for finding what each option does.

Oh, and on the following:
> **applebai said:**
> For a admin, it is necessary to have a server partition tool such as **url snipped**
I would disagree and say that this is unnecessary, as partitioning does not normally change and it certainly would not be done remotely. There are free tools available to do all of what that product claims to do. Advertising is not allowed here.

---

