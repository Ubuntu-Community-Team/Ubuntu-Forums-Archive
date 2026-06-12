---
title: "Logs to take into account"
date: 2012-01-19
forum: Server Platforms
---

### Post by Darthcolo on 2012-01-19
Hi all.
I would like to know which ones are the logs that I have to take into account when I am using a full ubuntu server implementation.

Thanks!

---

### Post by Habitual on 2012-01-19
/var/log/*

---

### Post by Lars Noodén on 2012-01-19
Habitual is right.  But you have to start somewhere, so start with [font=Courier New]/var/log/auth.log[/font] and [font=Courier New]/var/log/syslog[/font]

If you're running services (e.g. mail or web service) learn those log files next.  You want to familiarize yourself with how to read the normal traffic.

---

### Post by Darthcolo on 2012-01-19
Great! thanks! :D

---

