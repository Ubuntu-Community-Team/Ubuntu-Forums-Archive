---
title: "Another kernel bug in CIFS?"
date: 2009-06-17
forum: Server Platforms
---

### Post by bolexina on 2009-06-17
Hi all,

I have 8.04 ubuntu system with latest provided kernel (2.6.24-23-generic #1 SMP Wed Apr 1 21:43:24 UTC 2009 x86_64 GNU/Linux)

Few moments ago I got a complete system lockup. What I can find in logs is:
Jun 17 05:37:44 forum-db kernel: [    0.000000]  CIFS VFS: No response for cmd 162 mid 44079
Jun 17 05:38:44 forum-db kernel: [    0.000000]  CIFS VFS: server not responding
Jun 17 05:38:44 forum-db kernel: [    0.000000]  CIFS VFS: No response for cmd 162 mid 44085
Jun 17 05:39:44 forum-db kernel: [    0.000000]  CIFS VFS: server not responding
Jun 17 05:39:44 forum-db kernel: [    0.000000]  CIFS VFS: No response for cmd 162 mid 44091
Jun 17 05:40:44 forum-db kernel: [    0.000000]  CIFS VFS: server not responding
Jun 17 05:40:44 forum-db kernel: [    0.000000]  CIFS VFS: No response for cmd 162 mid 44097
Jun 17 05:40:47 forum-db kernel: [    0.000000] BUG: scheduling while atomic: cp/20245/0xffffffff

I've found [http://git.kernel.org/gitweb.cgi?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=a403a0a370946e7dbcda6464a3509089daee54bc](http://git.kernel.org/gitweb.cgi?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=a403a0a370946e7dbcda6464a3509089daee54bc) but this patch seems already applied to the current kernel. 

Some ideas?

Thanks.

---

