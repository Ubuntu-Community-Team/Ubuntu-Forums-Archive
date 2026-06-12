---
title: "FASTCGI Errors"
date: 2012-12-20
forum: Server Platforms
---

### Post by picosam on 2012-12-20
Hello all, I have this in my /var/log/apache2/error.log file :

```
[Thu Dec 20 16:10:37 2012] [notice] caught SIGTERM, shutting down
[Thu Dec 20 16:10:37 2012] [alert] (4)Interrupted system call: FastCGI: read() from pipe failed (0)
[Thu Dec 20 16:10:37 2012] [alert] (4)Interrupted system call: FastCGI: the PM is shutting down, Apache seems to have disappeared - bye
[Thu Dec 20 16:10:37 2012] [notice] FastCGI: process manager initialized (pid 854)
[Thu Dec 20 16:10:37 2012] [notice] Apache/2.2.22 (Ubuntu) DAV/2 SVN/1.7.5 mod_fastcgi/mod_fastcgi-SNAP-0910052141 mod_ssl/2.2.22 OpenSSL/1.0.1c configured -- resuming normal operations

```

Any idea what this means?

Thanks,
Sammy

---

