---
title: "History"
date: 2008-05-22
forum: Server Platforms
---

### Post by quikone8 on 2008-05-22
I was wondering if there is any way to pull up a history of updates and synaptic additions to the system.  I have had an update problem and think it could possibly be a problem with an added package.  I would like to remove some of them one/one to find out which one it could be.  It also seems as if the system is running slow.  I can open add/remove, but not update or synaptic.

Thanks,

---

### Post by samosamo on 2008-05-23
you know you should've checked your log dir...

/var/log/apt/term.log

---

### Post by MJN on 2008-05-23
I'm not familiar with Apt's term.log but I use the **/var/log/dpkg***logs for tracking package installs etc.

For those done with Synaptic, you'll find the history in Synaptic itself in File > History.

What's the actual problem you're trying to solve?

Mathew

---

### Post by quikone8 on 2008-05-31
I did solve it, it finally crashed hard and I reinstalled the system.  This time I will be very careful what and how I install packages.

---

