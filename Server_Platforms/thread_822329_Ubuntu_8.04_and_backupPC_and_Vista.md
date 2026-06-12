---
title: "Ubuntu 8.04 and backupPC and Vista"
date: 2008-06-08
forum: Server Platforms
---

### Post by ispyisail on 2008-06-08
Hi All

Has anybody successfully backed up a windows vista PC using Ubuntu 8.04 and backupPC installed from the repository.

In another fourm it has been suggested that there might be a bug between backupPC and the latest version of samba that ships with ubuntu 8.04.

```
> Ok, I have fixed this problem.  It seems that Fedora 9 ships with
> samba version 3.2.0-1.pre3.9, which does not work (for whatever
> reason) with BackupPC.  The fix is to download the latest STABLE
> source of samba (3.0.28a) and compile it yourself and then do a "make
> install" to replace the 3.2.0-1.pre3.9 binaries with the ones from
> stable.
```

I was wondering if someone could confirm of deny this rumour?

Thanks

---

### Post by ispyisail on 2008-06-09
I've done some research on my own question?

BackupPC version 3.0.0
Windows Vista Ultimate SP1
Samba  3.0.28a-1ubuntu4.1
Ubuntu 8.04 server sdition

Using the above versions  i can confirm that backupPC **can** back up shared folders from Windows vista machines

---

