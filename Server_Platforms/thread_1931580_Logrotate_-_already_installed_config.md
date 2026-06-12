---
title: "Logrotate - already installed config"
date: 2012-02-25
forum: Server Platforms
---

### Post by Michael_BoG on 2012-02-25
Hi,

I just noticed that my Ubuntu Server 10.04 dedicated server has something called logrotate installed. Out of my understanding, this is something that can move logs to *.1-10 and so on, and then replace the highest numbered ones with the previous and delete and so on. Anyhow, my actual question is weather the default configuration does this by default, or if I have to manually configure it, add it to a cronjob and so on.

Anyone know this?

---

### Post by CharlesA on 2012-02-25
It runs by default.

---

### Post by Michael_BoG on 2012-02-25
Aha, so everything is pretty much setup then? No need to configure for additional logs?

---

### Post by CharlesA on 2012-02-25
Shouldn't have to. It should run as a daily cronjob.

---

### Post by SeijiSensei on 2012-02-26
> **Michael_BoG said:**
> Aha, so everything is pretty much setup then? No need to configure for additional logs?

The configuration files for logrotate reside in /etc/logrotate.d.  A cron job runs the program once per day; it scans all the files and runs any rotations required according to the frequency (daily, weekly, etc.) specified in the configuration file.

You can have logrotate handle other files than the defaults simply by adding another configuration file to /etc/logrotate.d.

---

