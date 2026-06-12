---
title: "Strange server problem"
date: 2007-10-22
forum: Server Platforms
---

### Post by Wallace on 2007-10-22
I have a server running Ubuntu. It was running 7.04 without problem, and yesterday morning I upgraded it to 7.10. This went smoothly and all seemed well.

However twice since then, things have gone a bit odd. I can't login via SSH (I get login/password prompt, even the 'last login' and server banner, then nothing). I can't login directly on the server either (same thing happens). I can't connect to the MySQL server remotely. I can connect to the apache and postfix servers remotely.

On one occasion when this happened, I was able to login directly, but couldn't do much. 'top' didn't work, 'ps' worked and it showed loads of processes that shouldn't have been running - like every cron job that had earlier run hadn't exited.

A shutdown didn't work and I ended up pulling the power. Everything is working fine again after that (for a few hours anyway).

The syslog doesn't seem to show any indication of what went wrong to cause this. Is there anything I can do to help work out what's causing this?

---

