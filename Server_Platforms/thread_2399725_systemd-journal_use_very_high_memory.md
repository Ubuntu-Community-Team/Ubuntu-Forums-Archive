---
title: "systemd-journal use very high memory"
date: 2018-08-29
forum: Server Platforms
---

### Post by cnbiz850 on 2018-08-29
I set up a small cloud server with 1GB RAM for testing, and installed Ubuntu server 18.04 64bits on it.  I often notice that systemd-journal gradually hogs up more memory.  It starts with 2%, and after a couple days, gets over 20%.  I read about its configuration, and set RuntimeMaxUse=10M (which I believe is for limiting memory usage) in file /etc/systemd/journal.conf.  But it doesn't seem to help.  Would anyone please tell me what to do?

Its CPU usage is not much though.

---

