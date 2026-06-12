---
title: "Time control"
date: 2007-08-06
forum: Ubuntu Christian Edition
---

### Post by jonathan_1700 on 2007-08-06
I want to limit the internet time to my children

how to fix a limit of time ?

---

### Post by TravMan63 on 2007-08-09
I suppose you could do 'internet time' with a modification of the examples here:

[http://ubuntuforums.org/showthread.php?t=505876](http://ubuntuforums.org/showthread.php?t=505876)

for example - you could substitute 'firefox' (I'm not sure of the actual name) in this:

```
00 21 * * 1-6 /usr/bin/skill -KILL -u username #log off 9PM Mon-Sat
```

Some how you would need to get the process ID to kill firefox...

I'm not exactly sure how to do it - maybe

```
0021 * * 1-6 kill "ps aux|grep firefox"
``` ... but I'm betting that is NOT right.

The 1st example will log the user off, and other data on the page will disallow log ons

or you could also kill either eth0 or ra0 - depending if you are wired or wireless...

---- edit
PKILL (pkill) - will kill a process by name rather than by pid ... that MIGHT work!

---

