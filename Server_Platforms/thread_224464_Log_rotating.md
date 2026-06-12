---
title: "Log rotating"
date: 2006-07-28
forum: Server Platforms
---

### Post by jstritar on 2006-07-28
Ubuntu handles log rotating very nicely. Where can I find the script that does this (or the necessary syslog configurations)? Ideally I'd like to put it on my real server and rsync the logs to my local server, so I don't have to keep deleting a 2 gb apache access_log.

---

### Post by jstritar on 2006-07-29
Nobody knows?

---

### Post by mannheim on 2006-07-31
The scripts are /etc/cron.daily/sysklogd and /etc/cron.weekly/sysklogd. At least, that's where they are on my dapper installation.

---

