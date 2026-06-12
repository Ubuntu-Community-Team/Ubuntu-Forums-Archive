---
title: "dapper: cp does not preserve timestamp over NFS"
date: 2008-03-12
forum: Server Platforms
---

### Post by uba704 on 2008-03-12
Hi,

When using "cp" with the flag "-p" it does sometimes not preserve timestamps when a client user copies files over NFS. On the NFS server we have Ubuntu 6.06.2 LTS 2.6.15-51-server and the client uses Ubuntu 6.06.2 LTS 2.6.15-51-386.

Example:
$ ls -l test.text
-rw-r--r-- 1 user group 6 2008-03-12 22:15 test.text
$ cp -p test.text test.text2
$ ls -l test.text2
-rw-r--r-- 1 user group 6 2008-03-12 22:16 test.text2

Why is the timesstamp updated from 22:15 to 22:16 when I am using "-p"? Looks very strange to me. I have looked in both /var/log/messages and /var/log/daemon.log on both the server and the client and nothing shows up there.

Please if you have any idea.

---

### Post by uba704 on 2008-03-13
I can add to this that I have applied all available updates both on the server and the client (Ubuntu Dapper). I have seen this problem for about half a year now so apparently it is not a recent update that have gone wrong. The command "cp" is "/bin/cp" from the "coreutils" package. When I copy a file with "cp -p" on a local disk the timestamp is preserved, it is only over NFS it is not preserved.

Any ideas what might be wrong please?

---

### Post by MJN on 2008-03-13
It looks like this is an old Debian bug:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=340236](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=340236)

As the fix rippled through to to Ubuntu it will not have been backported to Dapper (as it is non-critical from a security perspective) and hence you could either upgrade or hunt for a workaround (one that springs to mind is using rsync).

Mathew

---

