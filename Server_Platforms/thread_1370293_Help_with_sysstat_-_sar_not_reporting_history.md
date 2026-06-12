---
title: "Help with sysstat - sar not reporting history"
date: 2010-01-02
forum: Server Platforms
---

### Post by lightsabersetc on 2010-01-02
I have just set up sysstat on my server and am attempting to get sar working. I have enabled monitoring in the sysstat config file, modified my crontab for sar monitoring (below):
 
#Crontab for sysstat
 #Activity reports culled and updated every 10 minutes everyday
 -*/10 *   * * *     root  /usr/lib/sa/sa1
 #Update log sar reports every day at 2330 hours
 30 23 * * *      root  /usr/lib/sa/sa2 –A

but every time I run the sar command, all i get is:

12:11:40 AM       LINUX RESTART

12:28:03 AM       LINUX RESTART


If i run sar 1 3 tho, everything is fine (below):

12:48:28 AM     CPU     %user     %nice   %system   %iowait    %steal     %idle
12:48:29 AM     all      3.43      0.00      0.98      0.00      0.00     95.59
12:48:30 AM     all      7.88      0.00      1.97      0.00      0.00     90.15
12:48:31 AM     all      1.48      0.00      1.48      0.00      0.00     97.04
Average:        all      4.26      0.00      1.48      0.00      0.00     94.26

I have googled the crap out of it, and cant manage to figure out why my load history is not getting recorded. Did i miss a step somewhere?

---

