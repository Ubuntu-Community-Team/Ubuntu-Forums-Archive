---
title: "root password change related data"
date: 2008-03-31
forum: Sun Sparc Users
---

### Post by dannyboy79 on 2008-03-31
you should be able to parse your /var/log/auth.log files and see something like this:

Mar 31 12:41:41 UBUNTU sudo:   daniel : TTY=pts/1 ; PWD=/dev ; USER=root ; COMMAND=/usr/bin/passwd root
Mar 31 12:41:52 UBUNTU passwd[25160]: (pam_unix) password changed for root
Mar 31 12:41:52 UBUNTU passwd[25160]: (pam_unix) Password for root was changed


unfortunately there will only be saved for so long before the log files get removed. the oldest logs may even be zipped up.

---

