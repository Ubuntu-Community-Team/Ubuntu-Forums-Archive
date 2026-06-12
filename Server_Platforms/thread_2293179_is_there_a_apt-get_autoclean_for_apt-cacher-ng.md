---
title: "is there a apt-get autoclean for apt-cacher-ng"
date: 2015-09-03
forum: Server Platforms
---

### Post by pqwoerituytrueiwoq on 2015-09-03
last time i ran out of space i just deleted all the cache
also if there is a way to clear out cache based on thed release that would be nice, eg no need to keep 13.03 cache when all system run 14.04

---

### Post by v3.xx on 2015-09-03
Where are you finding this file?

---

### Post by TheFu on 2015-09-03
There is a web interface to clean up apt-cacherng. It has a clean up task.
[http://istar:3142/acng-report.html](http://istar:3142/acng-report.html) is the location on my network.
* run the "count data"
* In the Expiration section - there are some checkboxes
* "Start Scan and/or Expiration" - button.
* when the scan completes - there is a "check all" checkbox at the bottom. Select it
* Delete selected files.  I had a few 404 errors ... 

Or you can just "Delete Unreferenced" on the first page.

---

### Post by pqwoerituytrueiwoq on 2015-09-03
> **TheFu said:**
> There is a web interface to clean up apt-cacherng. It has a clean up task.
[http://istar:3142/acng-report.html](http://istar:3142/acng-report.html) is the location on my network.
* run the "count data"
* In the Expiration section - there are some checkboxes
* "Start Scan and/or Expiration" - button.
* when the scan completes - there is a "check all" checkbox at the bottom. Select it
* Delete selected files.  I had a few 404 errors ... 

Or you can just "Delete Unreferenced" on the first page.
im getting a failed to create log file error message, results in the task being aborted
i assume this is a permissions error
what chmod/chown command do i need to use
i think it gets it own user name, and i am nto sure where the log goes

---

### Post by TheFu on 2015-09-04
Set this up years ago and don't remember having to do anything extra. Sorry.
With 4400 beans, I'll assume you know how to determine and solve permissions issues based on the process owner AND know where the log files are on a system. This should help:
```
istar:/var/log$ \ls -la apt-cacher-ng |more
total 37212
drwxr-sr-x  2 apt-cacher-ng apt-cacher-ng    12288 Sep  4 06:51 .
```

---

### Post by pqwoerituytrueiwoq on 2015-09-04
odd, still did not work so i chmod 666 ed it still wont work
```
~$ ls -la /var/log/apt-cacher-ng
total 8
drwxr-sr-x  2 apt-cacher-ng apt-cacher-ng 4096 Sep  4 19:00 .
drwxr-xr-x 13 root          root          4096 Sep  4 06:33 ..
-rw-rw-rw-  1 apt-cacher-ng apt-cacher-ng    0 Apr 11  2014 apt-cacher.err
-rw-rw-rw-  1 apt-cacher-ng apt-cacher-ng    0 Apr 11  2014 apt-cacher.log
```

---

### Post by TheFu on 2015-09-05
What do the log files say?

---

### Post by pqwoerituytrueiwoq on 2015-09-05
nothing at all *points at file size*

---

### Post by pqwoerituytrueiwoq on 2015-09-06
i had logging disabled, apparently this feature does not support that option
/etc/apt-cacher-ng/acng.conf

---

### Post by TheFu on 2015-09-06
So - solved? Please mark **solved** in thread tools to help others.

---

