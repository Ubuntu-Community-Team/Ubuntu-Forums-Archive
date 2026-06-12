---
title: "Problem : /usr/local/lib/libz.so.1: no version information available"
date: 2010-09-16
forum: Server Platforms
---

### Post by blindfold on 2010-09-16
Hi guys,

I'm running into this error with multiple applications.

sysadmin@ernie:~$ vi /etc/ld.so.conf
vi: /usr/local/lib/libz.so.1: no version information available (required by /usr/lib/libpython2.6.so.1.0)

( it does open vi and then the file specified )

or 

sysadmin@ernie:~$ ufw status
/usr/bin/python: /usr/local/lib/libz.so.1: no version information available (required by /usr/bin/python)

I have been looking arround for this error and have found some info, but nothing that keeps the error gone. When i delete the symlink in /usr/local/lib/libz.so.1 everythings works fine. But after running an ldconfig or installig something with apt the symlink get recreated and the problem returns.

sysadmin@ernie:~$ uname -a
Linux ernie.morethanlive.nl 2.6.32-24-server #42-Ubuntu SMP Fri Aug 20 15:38:55 UTC 2010 x86_64 GNU/Linux


Does anybody have a good idea ?

Thanks in advance,

cheers,

---

