---
title: "Dovecot issues: dovecot-auth"
date: 2011-11-29
forum: Server Platforms
---

### Post by carazeith on 2011-11-29
I have just set up all of my configuration files for Dovecot and Postfix. I had it all working and now after adding all of my virtual users i went to restart dovecot and log in.

However it seems that it is instantly killing itself on start up. So i went through the logs for it and found this error.

/var/log/dovecot
```
master: Fatal: service(auth) access(/usr/lib/dovecot/dovecot-auth) failed: No such file or directory
```Can anyone give me any advice on how to fix this at all as i have no idea where to start looking, google had nothing on this by what i could find?

The system is running 11.10 with all packages up to date.

---

### Post by carazeith on 2011-11-29
After a break i got this to work by creating the file and giving it the correct access for it to be run.

---

