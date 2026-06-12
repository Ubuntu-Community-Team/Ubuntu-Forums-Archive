---
title: "Missing /lib/modules for current kernel"
date: 2011-11-30
forum: Server Platforms
---

### Post by zachlac on 2011-11-30
Kernel: Linux 2.6.35-std210-amd64 #2 SMP Fri Apr 1 21:13:29 UTC 2011 x86_64 GNU/Linux

/lib/modules:
2.6.31-22-server  2.6.32-26-server  2.6.32-27-server  2.6.32-28-server  2.6.32-29-server  2.6.32-30-server  2.6.32-31-server  2.6.32-32-server  2.6.32-33-server  2.6.32-34-server  2.6.32-35-server

It looks like I'm missing all of the /lib/modules folders for all of my recent kernel upgrades.

Any idea how to get these: running "depmod -a" gives me:
WARNING: Couldn't open directory /lib/modules/2.6.35-std210-amd64: No such file or directory
FATAL: Could not open /lib/modules/2.6.35-std210-amd64/modules.dep.temp for writing: No such file or directory

---

