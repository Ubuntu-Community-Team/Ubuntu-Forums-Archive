---
title: "Latest Filezilla client cannot connect to pureftpd using TLS"
date: 2019-07-24
forum: Server Platforms
---

### Post by bluexmas on 2019-07-24
Context: Latest Filezilla client version fails to connect to Ubuntu 18.04 pureftpd from official repo with the error:

```
Error: GnuTLS error -110 in gnutls_record_recv: The TLS connection was non-properly terminated.
```

It seems that the issue is:
1/ Pureftp advertises capability to use TLS v1.3
2/ Filezilla tries to connect using TLS v1.3 and fails, because pureftpd server doesn't actually support this, only advertises it.

There is a bug filed here:
[https://bugs.launchpad.net/ubuntu/+source/pure-ftpd/+bug/1832998](https://bugs.launchpad.net/ubuntu/+source/pure-ftpd/+bug/1832998)

I don't see a good solution to build pureftpd from source. IMHO Filezilla devs should have wait until most used ftp servers are patched in the official repos. This really creates unnecessary tension between clients and servers maintainers.

I had to advise clients to stop using Filezilla and switch to another FTP client, and issued a statement that Filezilla is not supported anymore.

How do you guys manage this?

---

