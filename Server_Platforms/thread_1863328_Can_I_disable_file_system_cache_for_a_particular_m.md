---
title: "Can I disable file system cache for a particular mount?"
date: 2011-10-17
forum: Server Platforms
---

### Post by andor2 on 2011-10-17
Hi everyone,

I want to disable file system caching for a particular file system mount. For ex., when I am mounting /dev/sdb, I use:

mount /dev/sdb /mount/dir

Can I input some options to this command such that files accessed from the mounted file system are not cached at all by the OS?

Motivation for doing this: 

I am building an application, which needs to do its own buffering of data in files. When I measure performance numbers for my application, it is running unusually fast because read I/O requests are not touching the disk; instead they are served off the file system cache.

BTW, I don't prefer to use O_DIRECT flag while opening files.

Thanks
AO2

---

