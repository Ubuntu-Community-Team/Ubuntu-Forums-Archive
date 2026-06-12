---
title: "sysctl -w kernel.shmmax= fails to survive a reboot"
date: 2012-02-13
forum: Server Platforms
---

### Post by saphil on 2012-02-13
sysctl -w kernel.shmmax=120337984
is required to get my highly ptuned postgresql-9.1 server to start on a 10.04 LTS server.
From what I have found, the -w is supposed to stand for "write to system config file" not "well, it might happen if you wish hard enough."

What am I doing -wrong?

---

### Post by Toz on 2012-02-13
-w makes the change temporarily for the current boot. To make it permanent, add it to the end of /etc/sysctl.conf:
```
kernel.shmmax = 120337984
```

---

### Post by saphil on 2012-02-13
Thanks! I have read that before but since that file is full of network packet-handling directives and nothing else, it seemed unlikely.

I will try it and see :-)

Wolf

---

