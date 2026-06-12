---
title: "Server Non Responsive for 12 hours"
date: 2008-04-21
forum: Server Platforms
---

### Post by awreneau on 2008-04-21
I have a 6.06 LTS server running postfix as an internal mail relay.  I have a situation where twice it chokes and stops logging anything.  Yet all the while the server is reachable by pinging, while SMTP is offline.  The only reason I know it's reachable via ping is b/c Whats Up Pro is showing available.  It generally happens in the early morning hours when nothing is going on and Whats Up Pro generates and email and creates a ticket so we know about the smtp outage.

Anyway, I've have checked every log file in /var/logs and everything stops reporting at 3:18 am.  Then when I logged in yesterday and rebooted logging begins again.

I thought a cron job might be causing problems but none run around this time.

cron.hourly runs at 17 minutes after each hour but nothing is setup for hourly runs.

cron.daily runs 6:25 am each day

cron.weekly runs at 6:47 am each sunday

cron.monthly runs at 6:52 am 1st day of the month.


I'm lost as to why this is happening.



The Server is running as a VM in ESX.


WR

---

### Post by awreneau on 2008-04-23
bump

---

