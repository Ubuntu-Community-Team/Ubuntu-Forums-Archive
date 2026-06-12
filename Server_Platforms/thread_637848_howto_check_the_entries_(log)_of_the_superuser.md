---
title: "howto check the entries (log) of the superuser?"
date: 2007-12-11
forum: Server Platforms
---

### Post by adhg on 2007-12-11
Hi experts,

I wonder if there's a way to check entries of SU in the system? In other words, I'm looking for a log file of SU entries (last 10 entries or so)

thanks 

* Yes, I have su rights :-)

---

### Post by p_quarles on 2007-12-11
They should all be recorded in /var/log/auth.log and its archives.

---

### Post by adhg on 2007-12-11
Great,
I see a lot of this message:

Dec  9 13:09:01 localhost CRON[11505]: (pam_unix) session opened for user root by (uid=0)
Dec  9 13:09:01 localhost CRON[11505]: (pam_unix) session closed for user root

what does that mean: uid=0? 

cron? does it mean it the system? trying to get in?

thanks for any pointers

---

### Post by MJN on 2007-12-11
Every system user has an associated UID (user identifier) number - indeed the system generally uses UIDs, the user name is more for us humans to comprehend easier. The root user is always UID 0.

The entries you're seeing are simply CRON entries, i.e. scheduled tasks being executed.  Cron runs as root as it often has to perform tasks that only root can do e.g. rotating logs and other system-operation type activities.

Hence, in this case it is nothing to worry about and is something you'd see on any system.

Mathew

---

