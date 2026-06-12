---
title: "Scheduled daemon restart"
date: 2010-10-18
forum: Server Platforms
---

### Post by dukiman on 2010-10-18
Hi,

Is there a way to restart a deamon with an scheduled event?

I would like to restart a deamon every day at a given hour.


Regerds,
Dušan

---

### Post by Ryan Dwyer on 2010-10-18
Use cron to run whatever command is required to restart the daemon.

Search the internet for /etc/crontab to find how to use it.

---

### Post by dukiman on 2010-10-18
Thanks Ryan that was exactly what i needed.

---

