---
title: "maildrop howto?"
date: 2006-12-10
forum: Server Platforms
---

### Post by xiaoxin on 2006-12-10
I am setting up a mail server.
I have a running postfix+dovecot+mysql. Going to add getmail for that to work properly need a working maildrop.
I can't get it running, i have authlib and the authlibmysql module set up following the docs. but maildrop is a no go.
errors like "Permission denied /usr/bin/maildrop: Cannot set my user or group id" or " authdaemon: s_connect() failed: Permission denied Invalid user specified." are in the mail.log after i change things in master.cf
anybody got some hints or a howto on how to get this working?

---

