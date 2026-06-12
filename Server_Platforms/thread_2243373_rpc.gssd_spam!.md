---
title: "rpc.gssd spam!"
date: 2014-09-08
forum: Server Platforms
---

### Post by richard51 on 2014-09-08
I have noticed recently, that the **syslog**, on all the client machines are full of **rpc.gssd** spam.

```

**syslog:**
Sep 8 14:26 pc13 rpc.gssd[432]: ERROR: failed to read service info
Sep 8 14:26 pc13 rpc.gssd[432]: ERROR: can't open /run/rpc_pipefs/gssd/clntXX/info
Sep 8 14:26 pc13 rpc.gssd[432]: ERROR: failed to read service info
Sep 8 14:26 pc13 rpc.gssd[432]: ERROR: can't open /run/rpc_pipefs/gssd/clntXX/info
Sep 8 14:26 pc13 rpc.gssd[432]: ERROR: failed to read service info
Sep 8 14:26 pc13 rpc.gssd[432]: ERROR: can't open /run/rpc_pipefs/gssd/clntXX/info
...

```

GSSAPI credentials works fine, i.e logging into ldap, autofs-ldap automounts, etc! I cannot see a point to these errors, there is no **/run/rpc_pipefs/gssd/****clntXX/info** file, and I believe that this error, and the **info** file are redundant. Is there a fix for this spam? The client machines are using Ubuntu 14.04 desktop.

---

### Post by richard51 on 2014-09-10
**Note:** This **bug** has now been fixed (*10th of September 2014*), just apply the latest updates!

**Please ignore my previous comment, I spoke too soon... rpc.gssd is still spamming the log file. But, there is a fix that will be released soon (*apparently*).**

---

