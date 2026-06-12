---
title: "sudo -i does not start new PAM session?"
date: 2018-03-06
forum: Security
---

### Post by AnrDaemon on 2018-03-06
I just noticed that when I "sudo -iu <someuser>", PAM settings do not kick in, particularly map_umask, leaving it the root (or sudoer's) umask.
Is this normal?

---

### Post by AnrDaemon on 2018-03-06
NVM got it.
```
su - <someuser>
```
starts a new session all proper.

---

