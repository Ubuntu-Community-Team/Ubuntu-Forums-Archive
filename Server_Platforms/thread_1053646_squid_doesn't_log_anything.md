---
title: "squid doesn't log anything"
date: 2009-01-28
forum: Server Platforms
---

### Post by and12345 on 2009-01-28
somehow when i open /var/log/squid/access.log there's nothing written inside it,

but in cache.log

2009/01/29 08:18:38| Starting Squid Cache version 2.7.STABLE3 for i386-debian-linux-gnu...
2009/01/29 08:18:38| Process ID 4114
2009/01/29 08:18:38| With 1024 file descriptors available
2009/01/29 08:18:38| Using epoll for the IO loop
2009/01/29 08:18:38| DNS Socket created at 0.0.0.0, port 42798, FD 6
2009/01/29 08:18:38| Adding nameserver 10.0.0.4 from squid.conf
2009/01/29 08:18:38| Adding nameserver 203.130.206.250 from squid.conf
2009/01/29 08:18:38| User-Agent logging is disabled.
2009/01/29 08:18:38| Referer logging is disabled.
2009/01/29 08:18:38| logfileOpen: opening log /var/log/squid/access.log
2009/01/29 08:18:38| Unlinkd pipe opened on FD 11
2009/01/29 08:18:38| Swap maxSize 102400 KB, estimated 7876 objects
2009/01/29 08:18:38| Target number of buckets: 393
2009/01/29 08:18:38| Using 8192 Store buckets
2009/01/29 08:18:38| Max Mem  size: 8192 KB
2009/01/29 08:18:38| Max Swap size: 102400 KB
2009/01/29 08:18:38| Local cache digest enabled; rebuild/rewrite every 3600/3600 sec
2009/01/29 08:18:38| logfileOpen: opening log /var/log/squid/store.log
2009/01/29 08:18:38| Rebuilding storage in /var/spool/squid (DIRTY)
2009/01/29 08:18:38| Using Least Load store dir selection
2009/01/29 08:18:38| Set Current Directory to /var/spool/squid
2009/01/29 08:18:38| Loaded Icons.
2009/01/29 08:18:38| Accepting proxy HTTP connections at 0.0.0.0, port 8080, FD 13.
2009/01/29 08:18:38| Accepting ICP messages at 0.0.0.0, port 3130, FD 14.
2009/01/29 08:18:38| HTCP Disabled.
2009/01/29 08:18:38| WCCP Disabled.
2009/01/29 08:18:38| Ready to serve requests.
2009/01/29 08:18:38| Done reading /var/spool/squid swaplog (0 entries)
2009/01/29 08:18:38| Finished rebuilding storage from disk.
2009/01/29 08:18:38|         0 Entries scanned
2009/01/29 08:18:38|         0 Invalid entries.
2009/01/29 08:18:38|         0 With invalid flags.
2009/01/29 08:18:38|         0 Objects loaded.
2009/01/29 08:18:38|         0 Objects expired.
2009/01/29 08:18:38|         0 Objects cancelled.
2009/01/29 08:18:38|         0 Duplicate URLs purged.
2009/01/29 08:18:38|         0 Swapfile clashes avoided.
2009/01/29 08:18:38|   Took 0.7 seconds (   0.0 objects/sec).
2009/01/29 08:18:38| Beginning Validation Procedure
2009/01/29 08:18:38|   Completed Validation Procedure
2009/01/29 08:18:38|   Validated 0 Entries
2009/01/29 08:18:38|   store_swap_size = 0k
2009/01/29 08:18:39| storeLateRelease: released 0 objects

and in my store.log

1233130322.677 RELEASE -1 FFFFFFFF 05DECB2A15E6EF4EAE5FAFC15927EF2A  200 1233126722 1233126722 1233130322 application/cache-digest 144/144 GET internal://gmsmyhome/squid-internal-periodic/store_digest
1233133922.687 RELEASE -1 FFFFFFFF 77BC116381156801C7B11EA15877C44B  200 1233130322 1233130322 1233133922 application/cache-digest 144/144 GET internal://gmsmyhome/squid-internal-periodic/store_digest
1233137522.697 RELEASE -1 FFFFFFFF 7991B4728CE6E2D6C2E46C383EB5F23F  200 1233133922 1233133922 1233137522 application/cache-digest 144/144 GET internal://gmsmyhome/squid-internal-periodic/store_digest
1233141122.707 RELEASE -1 FFFFFFFF 462A9C03F102D35119F0AFD400920DA4  200 1233137522 1233137522 1233141122 application/cache-digest 144/144 GET internal://gmsmyhome/squid-internal-periodic/store_digest
1233144722.717 RELEASE -1 FFFFFFFF 9B9E9FECA5B8DC7BE02037DDF3EC727A  200 1233141122 1233141122 1233144722 application/cache-digest 144/144 GET internal://gmsmyhome/squid-internal-periodic/store_digest
1233148322.727 RELEASE -1 FFFFFFFF 22A727261EC640C1E83A8DE8CD5F829D  200 1233144722 1233144722 1233148322 application/cache-digest 144/144 GET internal://gmsmyhome/squid-internal-periodic/store_digest
1233195518.713 RELEASE -1 FFFFFFFF 5D496D695FE867E44DE7A3FDBCF008AE  200 1233191918 1233191918 1233195518 application/cache-digest 144/144 GET internal://myhomeubuntuserverbo/squid-internal-periodic/store_digest

how do i know whether my squid running or not, coz i don't feel much difference with before using squid...

and when i generate report from webmin...

Now generating Sarg report from Squid log file /var/log/squid/access.log and all rotated versions ..

sarg -l /var/log/squid/access.log 
SARG: No records found
SARG: End

.. Sarg finished, but no report was generated. See the output above for details.

all clients can access internet and my squid proxy act as transparent proxy

---

