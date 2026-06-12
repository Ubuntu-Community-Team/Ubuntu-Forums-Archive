---
title: "ntop will not launch"
date: 2009-04-18
forum: Server Platforms
---

### Post by bluethundr on 2009-04-18
I am attempting to launch ntop for the first time and getting this result. 

```

DNS:/usr/sbin# ./ntop --set-admin-password
Sat Apr 18 18:07:32 2009  NOTE: Interface merge enabled by default
Sat Apr 18 18:07:32 2009  Initializing gdbm databases
Sat Apr 18 18:07:32 2009  **ERROR** ....open of /var/lib/ntop/prefsCache.db failed: Can't be writer
Sat Apr 18 18:07:32 2009  Possible solution: please use '-P <directory>'
Sat Apr 18 18:07:32 2009  **FATAL_ERROR** GDBM open failed, ntop shutting down...
Sat Apr 18 18:07:32 2009  CLEANUP[t3062364736]: ntop caught signal 2
Sat Apr 18 18:07:32 2009  THREADMGMT[t3062364736]: ntop RUNSTATE: SHUTDOWN(7)
Sat Apr 18 18:07:32 2009  CLEANUP[t3062364736] catching thread is unknown
Sat Apr 18 18:07:32 2009  CLEANUP: Running threads
Sat Apr 18 18:07:32 2009  CLEANUP: Locking purge mutex (may block for a little while)
Sat Apr 18 18:07:32 2009  CLEANUP: Locked purge mutex, continuing shutdown
Sat Apr 18 18:07:32 2009  CLEANUP: Continues
Sat Apr 18 18:07:32 2009  PLUGIN_TERM: Unloading plugins (if any)
Sat Apr 18 18:07:32 2009  CLEANUP: Clean up complete
Sat Apr 18 18:07:32 2009  THREADMGMT[t3062364736]: ntop RUNSTATE: TERM(8)
Sat Apr 18 18:07:32 2009  ===================================
Sat Apr 18 18:07:32 2009          ntop is shutdown...        
Sat Apr 18 18:07:32 2009  ===================================

```


This is a listing of the /var/lib/ntop directory.


```

-rw-r----- 1 ntop root   14399 2009-04-18 17:54 addressQueue.db
-rw-r----- 1 ntop root   45969 2009-04-18 18:07 dnsCache.db
-rw-r----- 1 ntop root  237568 2009-04-17 20:05 fingerprint.db
-rw-r--r-- 1 ntop root      30 2009-04-17 22:37 init.cfg
-rw-r----- 1 ntop root   12288 2009-04-17 20:05 LsWatch.db
-rw-r----- 1 ntop root 1110238 2009-04-17 20:00 macPrefix.db
-rw-r----- 1 ntop root   12546 2009-04-17 20:05 ntop_pw.db
-rwxrwxrwx 1 ntop root   12918 2009-04-17 20:05 prefsCache.db

```

Suggestions? Thx.

---

