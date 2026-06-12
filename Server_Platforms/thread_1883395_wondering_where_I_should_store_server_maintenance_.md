---
title: "wondering where I should store server maintenance scripts."
date: 2011-11-19
forum: Server Platforms
---

### Post by bvz on 2011-11-19
I am writing a couple of simple bash scripts that will be run by cron to do basic maintenance on my home server.  Where should I be saving these scripts?  Is there a preferred directory?

Thanks

---

### Post by Habitual on 2011-11-19
I stick mine in /root/scripts (which I have to make).

---

### Post by n00b2u on 2011-11-19
The "standard" (and I use this term loosely) would be to put them in /usr/local/bin, or some other directory under /usr/local.

---

### Post by SeijiSensei on 2011-11-19
I put them in /usr/local/sbin since they're designed to be run by root.  Like /bin and /usr/bin, /usr/local/bin is intended for programs available to all users.  /sbin, /usr/sbin, and /usr/local/sbin contain programs used by the system administrator.

---

### Post by bvz on 2011-11-19
> **SeijiSensei said:**
> I put them in /usr/local/sbin since they're designed to be run by root.  Like /bin and /usr/bin, /usr/local/bin is intended for programs available to all users.  /sbin, /usr/sbin, and /usr/local/sbin contain programs used by the system administrator.

Excellent.  Thanks for the info and the reply.

---

