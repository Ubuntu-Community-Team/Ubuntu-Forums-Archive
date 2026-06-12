---
title: "[SOLVED] Need help with Ntop"
date: 2007-04-20
forum: Server Platforms
---

### Post by wormser on 2007-04-20
I installed ntop and I am having problems getting it running.  It seems to be a permissions error.  Every command like sudo ntop -A brings back the same error.

> Thu Apr 19 23:05:51 2007  NOTE: Interface merge enabled by default
Thu Apr 19 23:05:51 2007  Initializing gdbm databases
Thu Apr 19 23:05:51 2007  **ERROR** ....open of /var/lib/ntop/prefsCache.db failed: File open error
Thu Apr 19 23:05:51 2007  Possible solution: please use '-P <directory>'
Thu Apr 19 23:05:51 2007  **FATAL_ERROR** GDBM open failed, ntop shutting down...
Thu Apr 19 23:05:51 2007  CLEANUP[t3057043664]: ntop caught signal 2
Thu Apr 19 23:05:51 2007  THREADMGMT[t3057043664]: ntop RUNSTATE: SHUTDOWN(7)
Thu Apr 19 23:05:51 2007  CLEANUP[t3057043664] catching thread is MAIN
Thu Apr 19 23:05:51 2007  CLEANUP: Running threads
Thu Apr 19 23:05:51 2007  CLEANUP: Locking purge mutex (may block for a little while)
Thu Apr 19 23:05:51 2007  CLEANUP: Locked purge mutex, continuing shutdown
Thu Apr 19 23:05:51 2007  CLEANUP: Continues
Thu Apr 19 23:05:51 2007  PLUGIN_TERM: Unloading plugins (if any)
Thu Apr 19 23:05:51 2007  CLEANUP: Clean up complete
Thu Apr 19 23:05:51 2007  THREADMGMT[t3057043664]: ntop RUNSTATE: TERM(8)
Thu Apr 19 23:05:51 2007  ===================================
Thu Apr 19 23:05:51 2007          ntop is shutdown...        
Thu Apr 19 23:05:51 2007  ===================================


The 3rd line makes me believe it is a permissions error.

This is the file permissions.

> drwxr-x---   2 ntop          root           264 2007-04-19 22:30 ntop

It looks like ntop created its own user.  I do not want to run it as root.  What would be the proper set up to get it working with a sudo?  

Thanks

---

### Post by wormser on 2007-04-20
I rebooted and it works!

---

