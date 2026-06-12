---
title: "ntpd unprivileged port"
date: 2008-11-25
forum: Server Platforms
---

### Post by Smatchimo on 2008-11-25
Hi,

We have been using cron jobs to call 'ntpdate -u (ntp server)' which works fine. However we'd like to switch to running ntpd instead for more continuous time syncing. The problem is ntpd doesn't seem to have a -u option like ntpdate and I can't seem to find any way to make it use an unprivileged port. A lot of our servers require the -u option or they can't talk to our NTP servers. Does anyone know how to make ntpd use an unprivileged port or is it really impossible?

Thanks!

---

