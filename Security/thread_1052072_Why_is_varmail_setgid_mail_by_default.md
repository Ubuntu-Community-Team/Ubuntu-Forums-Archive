---
title: "Why is /var/mail setgid mail by default?"
date: 2009-01-27
forum: Security
---

### Post by kalliergo on 2009-01-27
I'm sure there's a good reason, but I don't know what it is.  Why not give all processes rwx privileges for the directory?  Then, those that run without group mail privileges could set locks, etc.

Seems like the worst that could happen is that some process could write a random file to /var/mail.  Probably not a big deal and easily dealt with.

So, why setgid?

Thanks for any insight.

---

### Post by Agent ME on 2009-01-27
> **kalliergo said:**
> Then, those that run without group mail privileges could set locks, etc.
That right there. The point of the mail group is to set which users have privileges to it.

---

