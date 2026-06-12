---
title: "Backuppc with FC9/10 Clients"
date: 2011-06-15
forum: Server Platforms
---

### Post by kilroy423 on 2011-06-15
Hello,

I have configured Backuppc running on Ubuntu 10.10 server and have several backups configured.  I am using ssh over rsync.  Backups on other linux variants work fine, but with the FC9/10 I keep getting failures.  It appears that when the backuppc user logs in with keys and then executes the rsync command there is a weird character that is being returned, which causes backuppc to fail.  SELinux is not enabled, and I can't think of anything else it could be.  Has anyone else run into this problem?



Thanks

---

