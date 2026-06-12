---
title: "PureFTPd default permissions"
date: 2011-09-07
forum: Security
---

### Post by Alan Stainer on 2011-09-07
Okay, I have figured out I need a file called Umask in the /etc/pure-ftpd/conf/ directory. However, it doesn't appear to matter what I put in the file, the ftp server appears to hang and I am unable to connect to it.

I know it requires two octal numbers, should I be following a specific format? Any examples would help.

---

### Post by Alan Stainer on 2011-09-07
Fixed it. Usual value separate by a space.

---

