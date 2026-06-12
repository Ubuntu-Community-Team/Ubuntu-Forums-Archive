---
title: "Upgrade problem: dovecot will not start."
date: 2008-12-02
forum: Server Platforms
---

### Post by computx on 2008-12-02
I just upgraded my server from 8.04 to 8.10 and dovecot has stopped working.
I use maildirs in the users home directory and it is complaining that
 default_mail_env = maildir:~/.maildir
is an unknown setting. 
Didn't see any warnings about this in apt list changes.
Anyone know how to fix this?

---

### Post by computx on 2008-12-02
I guess the reason I didn't see it in the change log is that it happened way back in 7.04 and I had missed it then.
Anyway I discovered the new variable is mail_location =
not
default_mail_env =

---

