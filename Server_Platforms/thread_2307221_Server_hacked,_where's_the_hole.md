---
title: "Server hacked, where's the hole?"
date: 2015-12-22
forum: Server Platforms
---

### Post by fowie on 2015-12-22
This is the second time I've noticed this on an Ubuntu webserver I have running.  Suddenly pages stop working and when I go to investigate I find the root drive 100% full.  Closer inspection reveals that the /tmp folder is full of a bunch of folders with the names tmpXXXXXX which each seem to contain what looks like a firefox instance?
example:
```
total 13M
drwx------  17 root root 4.0K Dec 16 08:20 .
drwxrwxrwt 577 root root  32K Dec 22 21:27 ..
-rw-------   1 root root   24 Dec 16 08:20 addons.json
drwxr-xr-x   2 root root 4.0K Dec 16 08:20 amd64
-rw-r--r--   1 root root 185K Dec 16 08:20 blocklist.xml
drwx------   2 root root 4.0K Dec 16 08:20 bookmarkbackups
drwx------   4 root root 4.0K Dec 16 08:20 cache2
-rw-------   1 root root  64K Dec 16 08:20 cert8.db
-rw-------   1 root root  160 Dec 16 08:20 compatibility.ini
-rw-r--r--   1 root root 224K Dec 16 08:20 content-prefs.sqlite
-rw-r--r--   1 root root 512K Dec 16 08:20 cookies.sqlite
-rw-r--r--   1 root root  32K Dec 16 08:20 cookies.sqlite-shm
-rw-r--r--   1 root root 193K Dec 16 08:20 cookies.sqlite-wal
drwx------   3 root root 4.0K Dec 16 08:20 crashes
drwx------   2 root root 4.0K Dec 16 08:20 datareporting
-rw-------   1 root root 212K Dec 16 08:20 directoryLinks.json
drwxr-xr-x   3 root root 4.0K Dec 16 08:20 extensions
-rw-r--r--   1 root root  159 Dec 16 08:20 extensions.ini
-rw-------   1 root root 9.2K Dec 16 08:20 extensions.json
-rw-------   1 root root  35K Dec 16 08:20 frequencyCap.json
drwx------   3 root root 4.0K Dec 16 08:20 gmp
-rw-------   1 root root  16K Dec 16 08:20 key3.db
lrwxrwxrwx   1 root root   15 Dec 16 08:20 lock -> 127.0.1.1:+8637
-rw-r--r--   1 root root 3.7K Dec 16 08:20 mimeTypes.rdf
drwx------   2 root root 4.0K Dec 16 08:20 minidumps
-rw-r--r--   1 root root    0 Dec 16 08:20 .parentlock
-rw-r--r--   1 root root  96K Dec 16 08:20 permissions.sqlite
-rw-r--r--   1 root root  10M Dec 16 08:20 places.sqlite
-rw-r--r--   1 root root  32K Dec 16 08:20 places.sqlite-shm
-rw-r--r--   1 root root 129K Dec 16 08:20 places.sqlite-wal
-rw-------   1 root root 6.3K Dec 16 08:20 prefs.js
drwxr-xr-x   2 root root 4.0K Dec 16 08:20 safebrowsing
-rw-------   1 root root 122K Dec 16 08:20 search.json
-rw-------   1 root root   91 Dec 16 08:20 search-metadata.json
-rw-------   1 root root  16K Dec 16 08:20 secmod.db
-rw-------   1 root root   90 Dec 16 08:20 sessionCheckpoints.json
drwx------   2 root root 4.0K Dec 16 08:20 sessionstore-backups
-rw-r--r--   1 root root    0 Dec 16 08:20 SiteSecurityServiceState.txt
drwxr-xr-x   2 root root 4.0K Dec 16 08:20 startupCache
drwxr-xr-x   3 root root 4.0K Dec 16 08:20 storage
drwx------   2 root root 4.0K Dec 16 08:20 thumbnails
-rw-------   1 root root   25 Dec 16 08:20 times.json
-rw-r--r--   1 root root 3.3K Dec 16 08:20 user.js
drwxr-xr-x   2 root root 4.0K Dec 16 08:20 webapps
-rw-r--r--   1 root root  32K Dec 16 08:20 webappsstore.sqlite
-rw-r--r--   1 root root  32K Dec 16 08:20 webappsstore.sqlite-shm
-rw-r--r--   1 root root 161K Dec 16 08:20 webappsstore.sqlite-wal
drwxr-xr-x   2 root root 4.0K Dec 16 08:20 x86

```
There's also a .ICE_Unix folder (empty) and an .X10-lock and .X11-unix (and my server is headless).  All files are owned by root. It seems like the leak must be with something in Apache. Has anyone seen this hack before that could guide me as to how to plug the hole?

[EDIT]
Scratch my concerns about the .X11-unix, that's from an Xvfb process I was running...

---

### Post by darkod on 2015-12-23
1. Do you control packages/extensions installed or other people that have their own websites can add stuff? You need to look into things with known vulnerabilities like joomla, wordpress, etc... Is everything patched and most importantly, are default credentials changed. Recently I had a case where someone installed joomla and left the default credentials of admin/admin, and then got surprised when his webserver started sending spam... :) It took me a while to clean things up.

2. If you already don't have AV like clamav, install it and run a scan on the whole root partition.

That should be something to start with...

---

### Post by fowie on 2015-12-26
> **darkod said:**
> 1. Do you control packages/extensions installed or other people that have their own websites can add stuff? You need to look into things with known vulnerabilities like joomla, wordpress, etc... Is everything patched and most importantly, are default credentials changed. Recently I had a case where someone installed joomla and left the default credentials of admin/admin, and then got surprised when his webserver started sending spam... :) It took me a while to clean things up.

2. If you already don't have AV like clamav, install it and run a scan on the whole root partition.

That should be something to start with...

Thanks for the help,

1.  I control packages.  I'm guessing it's a wordpress install, but I have a few so I'm trying to figure out a way to track it down, auditctl picks up when the files are created, but doesn't show what the PID was, just that it was done by root...
2.  I run amavis, but I'm running an additional sweep of clamav just to be sure.

I changed my login credentials for root and my user and rebooted, and last is showing that I'm the only one that has logged in, so it must be some process inside the machine (could still be wordpress).

Is there a better way to figure out what PID is creating the files?

---

