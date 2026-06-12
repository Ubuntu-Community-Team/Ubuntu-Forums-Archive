---
title: "light weight syslogd front end"
date: 2016-02-18
forum: Server Platforms
---

### Post by NotQuiteSU on 2016-02-18
I'm looking for a lightweight front end for a syslog server. I only have 1 or 2 devices, and I'd hate to install something that would be resource intensive when it doesnt need to be. I just want to be able to casually look at logs, maybe search.

Ubuntu Server 14

---

### Post by MAFoElffen on 2016-02-18
my choices:
 - rsyslog to MySQL. Very light.
 - syslog-ng to MySQL. Scalable

When I say MySQL... that could also be Oracle dB... Once it is to an SQL database, then it is in a format where you can analyze and crunch metrics from easily. But... I've worked as a Sys Admin, dB Admin and Dev... so writing reports in SQL is something I feel comfortable with. 

Besides, then you can set dB table triggers to let you know when something is wrong or if you are cresting a threshold. Sure, you could do the same from scripts run from crontab, but triggers will tell you in real time (when the condition is met).

---

