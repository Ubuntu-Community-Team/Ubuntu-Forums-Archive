---
title: "Log size"
date: 2009-03-06
forum: Server Platforms
---

### Post by Cl0cKw0rK on 2009-03-06
I'm running ubuntu server 8.10. I'm getting a problem with my log files getting huge. specifically, the syslog, messages, and kern.log are growing until they take up the entire harddrive. any way i can set log size limits? I really don't want to set an hourly cron job to wipe them.
Thanks,
~Clockwork

---

### Post by LegendofTom on 2009-03-06
Use logrotate and its config file. There is also a script in cron.daily and also in cron.weekly called sysklogd. This script is responsible for rotating log files.

---

