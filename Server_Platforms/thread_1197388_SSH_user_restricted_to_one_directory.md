---
title: "SSH user restricted to one directory"
date: 2009-06-26
forum: Server Platforms
---

### Post by smeerbartje on 2009-06-26
Is it possible to create a user which is able to log-on via SSH and who can only have read-access to one specific directory on the file system? If so, can someone please give some hints ho to realize this?

---

### Post by prshah on 2009-06-26
> **smeerbartje said:**
> Is it possible to create a user which is able to log-on via SSH and who can only have read-access to one specific directory on the file system? If so, can someone please give some hints ho to realize this?

Theoretically speaking: (ie, it's your own fault if something breaks):

a) Setup a new non-privileged user, eg xferuser, with home directory. Create a group for him with the same name. Strip partnerships with other groups, including admin (which prevents use of sudo)

b) Add xferuser as an alloweduser and allowedgroup in /etc/ssh/sshd_config to allow SSH logon.

c) Set permissions on xferuser's home directory to r-x (read-no write-xecute) the "x" will allow listing the directory contents; if you disable this, he can only pull files to which he knows the exact name (case and all).

d) Once this is done, he need not even login; he can just use scp (secure copy) to pull the files he wants.

---

