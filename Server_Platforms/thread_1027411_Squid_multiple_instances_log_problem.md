---
title: "Squid multiple instances log problem"
date: 2009-01-01
forum: Server Platforms
---

### Post by Shwick2 on 2009-01-01
I'm trying to run multiple instances of squid and I've followed the available directions.

The second instance of squid throws an error when it tries to open it's access log file.
```

Jan  1 10:32:12 desktop squid[15527]: Squid Parent: child process 15529 started
Jan  1 10:32:12 desktop (squid): Cannot open '/var/log/squid3/accessSquid3HTTPProxy.log' for writing. ^IThe parent directory must be writeable by the ^Iuser 'proxy', which is the cache_effective_user ^Iset in squid.conf.
Jan  1 10:32:12 desktop squid[15527]: Squid Parent: child process 15529 exited with status 1
Jan  1 10:32:42 desktop squid[15540]: Exiting due to repeated, frequent failures

```
An "ls -l /var/log/squid3/" shows,
```

-rw-r----- 1 proxy proxy      0 2009-01-01 07:56 access.log
-rw-r----- 1 proxy proxy 118302 2008-12-31 20:46 access.log.1
-rw-r----- 1 proxy proxy      0 2009-01-01 10:29 accessSquid3HTTPProxy.log
-rw-r--r-- 1 proxy proxy   6773 2009-01-01 10:11 cache.log
-rw-r--r-- 1 proxy proxy 112239 2008-12-31 19:58 cache.log.1
-rw-r--r-- 1 proxy proxy   7005 2009-01-01 10:32 cacheSquid3HTTPProxy.log
-rw-r----- 1 proxy proxy    603 2009-01-01 09:58 store.log
-rw-r----- 1 proxy proxy 154882 2009-01-01 06:58 store.log.1

```

Why can't it write to it's log file when the first instance can write to it's log file and starts up properly?

---

