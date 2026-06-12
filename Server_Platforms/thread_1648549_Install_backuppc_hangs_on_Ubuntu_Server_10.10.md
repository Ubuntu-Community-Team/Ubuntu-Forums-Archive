---
title: "Install backuppc hangs on Ubuntu Server 10.10"
date: 2010-12-18
forum: Server Platforms
---

### Post by posterlion on 2010-12-18
Hello Forum,

Today I decided to install a BackupPc Server on Ubuntu 10.10, but the install would hang at the Postfix configuration screen.

Procedure that does not work:

Install Ubuntu Server 10.10
login first time
sudo aptitude install backuppc

install hangs at the email configuration screen.

Procedure that works:

Install Ubuntu Server 10.04
login first time
sudo aptitude install backuppc

installs perfectly
I am backing up as I type this post.

This looks like a bug in the install procedure for Backuppc.  If this is the wrong place to post this information, please direct me to the proper place.

Anyway, I've repeated this procedure twice and am sure I can recreate it at will.

Thanks in advance!

---

