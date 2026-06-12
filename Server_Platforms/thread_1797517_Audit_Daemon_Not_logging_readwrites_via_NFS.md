---
title: "Audit Daemon: Not logging read/writes via NFS"
date: 2011-07-05
forum: Server Platforms
---

### Post by panalk on 2011-07-05
Hi all,

I am using the auditd daemon to monitor read and write access to one of my directories. The rules are as follows:
LIST_RULES: exit,always dir=/data/dirToWatch (0xc) perm=r key=dataRead
LIST_RULES: exit,always dir=/data/dirToWatch (0xc) perm=wa key=dataWrite

auditd logs all read/write accesses that I do locally. The directory is however also exposed over NFS. If I know do a read/write from another server, this action does not show up in the logs.

I thought since I am watching the local filesystem, this would be recorded in any case, independent of the access method (local, NFS, ...). Why isn't it?

Do I have to adapt the rules so that NFS read/writes are logged as well?

Thanks for the help!

---

