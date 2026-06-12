---
title: "xfs service dieing but not restoring itself"
date: 2010-06-05
forum: Server Platforms
---

### Post by artooro on 2010-06-05
I'm running the XFS service on Ubuntu 10.04 and I have a bit of a problem. Every so often it just dies and the network stations cannot load the required fonts, and I have to login to the server and restart the XFS service

If I run the command "service xfs restart" I see the following:

```
Stopping X font server: xfs not running (removing stale /var/run/xfs/xfs.pid).
Setting up X font server socket directory /tmp/.font-unix...done.
Starting X font server: xfs.
```

So obviously the process became stale but it was not automatically restored.

Is there some way to fix this? Do I seriously have to write a script to check every minute to see if it's working and if not restart it?

---

