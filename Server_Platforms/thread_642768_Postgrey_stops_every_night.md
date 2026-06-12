---
title: "Postgrey stops every night"
date: 2007-12-17
forum: Server Platforms
---

### Post by Jengle on 2007-12-17
Does anyone know if there is a fix for Postgrey stopping every night?  I have a work around using Monit to restart it, but it is annoying that it stops at least 3 or 4 times every night.  Anyone have any suggestions?

---

### Post by HermanAB on 2007-12-17
It should not ever stop, unless something removes the mail log file.  Check your cron tasks.  Maybe logrotate renames the maillog?

Cheers,

Herman

---

### Post by ubnuturero on 2007-12-17
Take a look at 

[https://bugs.edge.launchpad.net/ubuntu/gutsy/+source/db4.4/+bug/153996](https://bugs.edge.launchpad.net/ubuntu/gutsy/+source/db4.4/+bug/153996)

Leonel

---

### Post by MJN on 2007-12-17
Does the mail log give any clue as to why it's stopping?

Mathew

---

### Post by Jengle on 2007-12-17
This is what I see in the mail log:

Dec 17 02:21:34 Ubuntu-1 postgrey[9671]: cleaning up old logs... 
Dec 17 02:21:34 Ubuntu-1 postgrey[9671]: cleaning up old entries... 
Dec 17 02:21:35 Ubuntu-1 postgrey[9671]: cleaning main database finished. before: 5764, after: 540 
Dec 17 02:21:35 Ubuntu-1 postgrey[9671]: fatal: Can't call method "txn_commit" on an undefined value at /usr/sbin/postgrey

---

### Post by MJN on 2007-12-17
That confirms it's the bug referenced by Leonel - so keep an eye on it.

Mathew

---

### Post by Jengle on 2007-12-17
Thanks for confirming that.  I looked at the link Leonel sent.  I must admit some of it lost me.  It doesn't look like there is a fix at this time.

Right now Monit restarts the service for me, but would be nice to have a cure.:confused:

Thanks,

---

### Post by HermanAB on 2007-12-17
Consider downgrading to a previous version of postgrey, till there is a fix for the latest version.

Cheers,

H.

---

