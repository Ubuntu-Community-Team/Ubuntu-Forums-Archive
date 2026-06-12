---
title: "Deleting large file but disk space not freed up"
date: 2009-02-06
forum: Server Platforms
---

### Post by stonneway on 2009-02-06
Hi chaps,

I've deleted two 35GB (logs from /var/logs) files from a server here via ssh using "sudo rm /var/log/whopper.log".

However, I did a check of disk space before using discus and after, and no disk space was freed up. So, we've removed 70GB or so of log files and are still low on space.

Any ideas why this might be ?

Olly

---

### Post by gombadi on 2009-02-06
The kernel will not free disk space of a deleted file until all file handles have been closed.

My guess is that syslog still has a file handle open for those files.

Restart the syslog process and have another look.

---

