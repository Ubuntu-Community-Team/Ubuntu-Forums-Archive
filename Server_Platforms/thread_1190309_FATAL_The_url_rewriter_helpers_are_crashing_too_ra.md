---
title: "FATAL: The url_rewriter helpers are crashing too rapidly, need help!"
date: 2009-06-17
forum: Server Platforms
---

### Post by marklodge on 2009-06-17
i installed squid and videocache
now when i try to start squid it does not start
i startd in debug mode and heres the output:

vpro:/home/ztel# /usr/sbin/squid -NCd10
2009/06/17 17:57:02| Starting Squid Cache version 2.7.STABLE3 for i386-debian-linux-gnu...
2009/06/17 17:57:02| Process ID 3284
2009/06/17 17:57:02| With 1024 file descriptors available
2009/06/17 17:57:02| Using epoll for the IO loop
2009/06/17 17:57:02| Performing DNS Tests...
2009/06/17 17:57:02| Successful DNS name lookup tests...
2009/06/17 17:57:02| DNS Socket created at 0.0.0.0, port 42584, FD 6
2009/06/17 17:57:02| Adding nameserver 10.0.0.2 from /etc/resolv.conf
2009/06/17 17:57:02| helperOpenServers: Starting 7 'python' processes
2009/06/17 17:57:03| User-Agent logging is disabled.
2009/06/17 17:57:03| Referer logging is disabled.
2009/06/17 17:57:03| logfileOpen: opening log /var/log/squid/access.log
2009/06/17 17:57:03| Unlinkd pipe opened on FD 18
2009/06/17 17:57:03| Swap maxSize 102400 KB, estimated 7876 objects
2009/06/17 17:57:03| Target number of buckets: 393
2009/06/17 17:57:03| Using 8192 Store buckets
2009/06/17 17:57:03| Max Mem  size: 8192 KB
2009/06/17 17:57:03| Max Swap size: 102400 KB
2009/06/17 17:57:03| Local cache digest enabled; rebuild/rewrite every 3600/3600 sec
2009/06/17 17:57:03| logfileOpen: opening log /var/log/squid/store.log
2009/06/17 17:57:03| Rebuilding storage in /var/spool/squid (CLEAN)
2009/06/17 17:57:03| Using Least Load store dir selection
2009/06/17 17:57:03| Set Current Directory to /var/spool/squid
2009/06/17 17:57:03| Loaded Icons.
2009/06/17 17:57:03| Accepting proxy HTTP connections at 0.0.0.0, port 3128, FD 20.
2009/06/17 17:57:03| Accepting proxy HTTP connections at 0.0.0.0, port 8000, FD 21.
2009/06/17 17:57:03| Accepting proxy HTTP connections at 0.0.0.0, port 8080, FD 22.
2009/06/17 17:57:03| Accepting proxy HTTP connections at 0.0.0.0, port 43210, FD 23.
2009/06/17 17:57:03| Accepting ICP messages at 0.0.0.0, port 3130, FD 24.
2009/06/17 17:57:03| HTCP Disabled.
2009/06/17 17:57:03| WCCP Disabled.
2009/06/17 17:57:03| Ready to serve requests.
2009/06/17 17:57:03| WARNING: url_rewriter #1 (FD 7) exited
2009/06/17 17:57:03| Done reading /var/spool/squid swaplog (5 entries)
2009/06/17 17:57:03| Finished rebuilding storage from disk.
2009/06/17 17:57:03|         5 Entries scanned
2009/06/17 17:57:03|         0 Invalid entries.
2009/06/17 17:57:03|         0 With invalid flags.
2009/06/17 17:57:03|         5 Objects loaded.
2009/06/17 17:57:03|         0 Objects expired.
2009/06/17 17:57:03|         0 Objects cancelled.
2009/06/17 17:57:03|         0 Duplicate URLs purged.
2009/06/17 17:57:03|         0 Swapfile clashes avoided.
2009/06/17 17:57:03|   Took 0.0 seconds ( 145.6 objects/sec).
2009/06/17 17:57:03| Beginning Validation Procedure
2009/06/17 17:57:03|   Completed Validation Procedure
2009/06/17 17:57:03|   Validated 5 Entries
2009/06/17 17:57:03|   store_swap_size = 20k
2009/06/17 17:57:03| WARNING: url_rewriter #3 (FD 9) exited
2009/06/17 17:57:03| WARNING: url_rewriter #2 (FD 8) exited
2009/06/17 17:57:03| WARNING: url_rewriter #5 (FD 11) exited
2009/06/17 17:57:03| Too few url_rewriter processes are running
2009/06/17 17:57:03| storeDirWriteCleanLogs: Starting...
2009/06/17 17:57:03|   Finished.  Wrote 5 entries.
2009/06/17 17:57:03|   Took 0.0 seconds (34246.6 entries/sec).
FATAL: The url_rewriter helpers are crashing too rapidly, need help!

-----------------
Please help

---

