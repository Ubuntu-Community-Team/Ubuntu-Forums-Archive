---
title: "Firewall inbuilt Safe Mode"
date: 2019-04-11
forum: Ubuntu Cloud and Juju
---

### Post by moussa116 on 2019-04-11
I have Ubuntu 18.04 server and I wonder if there is a way to setup firewall Safe Mode like here:
[https://wiki.freepbx.org/display/FPG/Safe+Mode](https://wiki.freepbx.org/display/FPG/Safe+Mode)

Thanks in advance.

---

### Post by TheFu on 2019-04-12
Not that I know, nothing exactly like that. There might be, but nobody uses it.  You could script it, if you like. Just put a counter file that increments at reboot. Check the timestamp on the file (stat) to decide.

Or you can setup fail2ban ssh filters to allow access from specific subnets and never block it from those IPs.  No need to reboot a system over some firewall issue.  Uptime with 10,000 users matters.

There's always console access. Always have a way to access to system console.

---

