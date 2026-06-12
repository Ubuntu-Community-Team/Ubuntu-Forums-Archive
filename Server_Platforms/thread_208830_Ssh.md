---
title: "Ssh"
date: 2006-07-04
forum: Server Platforms
---

### Post by rikoshay on 2006-07-04
Hi, 

I logged into my server the other day using SSH and I wanted to check the log today to see what IP address I logged in from for interests sake more than anything else. I'm having trouble locating the SSH logfiles. I'm probably being thick but if someone could point me int he right direction I'd appreciate it. I manage the SSH server through webmin if that makes any difference.

Cheers,

Rik

---

### Post by lurchi on 2006-07-04
perhaps /var/log/auth.log could show you the information you need.

---

### Post by rikoshay on 2006-07-05
Thanks Lurchi, auth.log gave the information I was looking for. I'm pretty sure there should be a seperate SSH log but i still can't find it.

---

### Post by lurchi on 2006-07-11
by default there isn't a special ssh-logfile, i think, so you should create one using syslog-daemon. "man syslog.conf" or "/etc/syslog.conf" should help you.

---

