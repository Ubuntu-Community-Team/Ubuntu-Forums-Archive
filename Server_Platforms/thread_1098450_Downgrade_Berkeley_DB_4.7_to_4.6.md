---
title: "Downgrade Berkeley DB 4.7 to 4.6?"
date: 2009-03-17
forum: Server Platforms
---

### Post by thebitguru on 2009-03-17
Hi,

Does anyone know if it is possible to downgrade a Berkeley DB?  I think my previous distro used 4.7, which I used to create an SVN repository, but now in ubuntu I can't do anything to it because it is using 4.6.

```

[thebitguru@visionary repo]$ svn ls file:///sto/oth/temp/repo/shahablab_copy/
svn: Unable to open an ra_local session to URL
svn: Unable to open repository 'file:///sto/oth/temp/repo/shahablab_copy'
svn: Berkeley DB error for filesystem '/sto/oth/temp/repo/shahablab_copy/db' while opening environment:

svn: DB_VERSION_MISMATCH: Database environment version mismatch
svn: bdb: Program version 4.6 doesn't match environment version 4.7
[thebitguru@visionary repo]$

```

I have tried 'svnadmin recover', but that seems to corrupt the repository.


```

[thebitguru@visionary repo]$ svnadmin recover shahablab
Repository lock acquired.
Please wait; recovering the repository may take some time...
svnadmin: DB_RUNRECOVERY: Fatal error, run database recovery
svnadmin: bdb: Program version 4.6 doesn't match environment version 4.7
svnadmin: bdb: Unacceptable log file shahablab/db/log.0000000009: unsupported log version 14
svnadmin: bdb: Invalid log file: log.0000000009: Invalid argument
svnadmin: bdb: PANIC: Invalid argument
[thebitguru@visionary repo]$ svn ls file:///sto/oth/temp/repo/shahablab
svn: Unable to open an ra_local session to URL
svn: Unable to open repository 'file:///sto/oth/temp/repo/shahablab'
svn: Berkeley DB error for filesystem '/sto/oth/temp/repo/shahablab/db' while opening environment:

svn: DB_RUNRECOVERY: Fatal error, run database recovery
svn: bdb: Unacceptable log file /sto/oth/temp/repo/shahablab/db/log.0000000009: unsupported log version 14
svn: bdb: Invalid log file: log.0000000009: Invalid argument
svn: bdb: PANIC: Invalid argument
svn: bdb: unable to join the environment
[thebitguru@visionary repo]$

```

Thanks.

---

### Post by thebitguru on 2009-03-18
I am all set.  My previous distro was archlinux.  So, I downloaded it's USB image, copied to a USB drive, booted, installed latest svn, dumped (svnadmin dump), copied to the Ubuntu server, and finally restored (svnadmin load).

Thanks anyways :D

---

