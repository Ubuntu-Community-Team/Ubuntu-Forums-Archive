---
title: "Services and run-levels"
date: 2009-11-23
forum: Server Platforms
---

### Post by Kevitivity on 2009-11-23
Whats the best way to manage what services start at boot time and what run-level.  I'm a former Sun and Redhat admin who is familiar with their specific tools (serviceconf on RedHat for example).

Does Ubuntu have anything like this?

---

### Post by sisco311 on 2009-11-23
To manage the SysV like init scripts you could use sysv-rc-conf, but in Karmic (9.10) most of the SysV scripts are replaced by [Upstart]("http://upstart.ubuntu.com/getting-started.html") jobs.

---

