---
title: "How do you recover a broken SSH session if not originally using screen?"
date: 2009-09-16
forum: Security
---

### Post by kevdog on 2009-09-16
Just wondering if dropped remote SSH sessions can be recovered if not using screen originally

---

### Post by lvlint67 on 2009-09-16
> **kevdog said:**
> Just wondering if dropped remote SSH sessions can be recovered if not using screen originally


"You can't reconnect to a broken ssh connection, and in fact it
should have killed all the processes you were running...."

[http://lists.centos.org/pipermail/centos/2006-September/027988.html](http://lists.centos.org/pipermail/centos/2006-September/027988.html)

---

### Post by The Cog on 2009-09-16
Agreed. Unless the process had been detatched from the ssh tty before the connection broke, it should have been killed by the OS. And if the process had been detatched or run with nohup, I don't know of any way to re-attach a new tty to the process.

---

