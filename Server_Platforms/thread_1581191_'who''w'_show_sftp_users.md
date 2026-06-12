---
title: "'who'/'w' show sftp users?"
date: 2010-09-24
forum: Server Platforms
---

### Post by SlugSlug on 2010-09-24
using who or w command you can see users logged in via ssh..

Is it possible to show users currently logged in via sftp? (ssh)

cheers,

---

### Post by CharlesA on 2010-09-24
I'll check.

Just ssh'd in:

```
charles@thor:~$ w
 11:55:32 up 2 days,  4:50,  1 user,  load average: 0.00, 0.06, 0.03
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
charles  pts/0    000-000-000-000. 11:55    0.00s  0.19s  0.00s w
```

SSH and SFTP in:

```
charles@thor:~$ w
 11:56:21 up 2 days,  4:51,  1 user,  load average: 0.00, 0.05, 0.02
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
charles  pts/0    000-000-000-000. 11:55    0.00s  0.19s  0.00s w

```

I guess the answer is no. :(

However, it is listed in auth.log:

```
Sep 24 11:55:30 thor sshd[13792]: Accepted publickey for charles from xxx.xxx.xxx.xxx port 1396 ssh2
Sep 24 11:55:30 thor sshd[13792]: pam_unix(sshd:session): session opened for user charles by (uid=0)
Sep 24 11:55:59 thor sshd[13888]: Accepted publickey for charles from xxx.xxx.xxx.xxx port 4331 ssh2
Sep 24 11:55:59 thor sshd[13888]: pam_unix(sshd:session): session opened for user charles by (uid=0)
Sep 24 11:55:59 thor sshd[13964]: subsystem request for sftp
Sep 24 11:57:19 thor sshd[13792]: pam_unix(sshd:session): session closed for user charles
Sep 24 11:57:21 thor sshd[13888]: pam_unix(sshd:session): session closed for user charles

```

---

### Post by SlugSlug on 2010-09-24
I figured that bit ;)

Am wondering is a hack or diff command would show sftp || mainly for my conky I'd like to see whos downloading..



ahh maybe a tailf auth.log


unless there is a better way.....

?

---

### Post by CharlesA on 2010-09-24
Using tail would probably work. That's what I did. :P

---

