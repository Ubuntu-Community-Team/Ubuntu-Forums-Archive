---
title: "cvs [pserver aborted]: bad auth protocol start:"
date: 2008-04-22
forum: Server Platforms
---

### Post by mmerlone on 2008-04-22
I am trying to set up a cvs server on Ubuntu 7.10. I just
```
aptitude install cvs
```
When trying to connect from the client (Eclipse plataform) it gets connection refused, so I think I should run the server:
```
root@marte:~# /usr/sbin/cvs-pserver
(just after I press return here)
cvs [pserver aborted]: bad auth protocol start:
root@marte:~#
```

If I run manually I get exaclty the same:

```
root@marte:~# /usr/bin/cvs -b /usr/bin --allow-root=/var/lib/cvs pserver
(just after I press return here)
cvs [pserver aborted]: bad auth protocol start:
root@marte:~#
```

The odd thing is that the error message just appears when I press return after the command.
I searched google and those forums but none got a clue of what is going on. Or am I misunderstanding everything? Can anyone please help1?

Thanks in advance.

---

### Post by a9k3d on 2009-05-14
From man cvs
> The cvs server and pserver commands are used to provide repository  access  to remote  clients and expect a client conversation on stdin & stdout.  Typically these commands are launched from inetd or via ssh (see node `Remote  repositories' in the CVS manual).

The current version doesn't setup up inetd or xinetd. From /usr/share/doc/cvs:
> For reference, a typical entry in inetd.conf would be:

cvspserver  stream  tcp  nowait.400  root  /usr/sbin/tcpd  /usr/sbin/cvs-pserver

The number 400 in the "nowait.400" section above configures the
allowed respawn rate in inetd, in invocations per minute. The default
value for the respawn rate is 40; if you expect to use the pserver a
lot (e.g. for large checkins or via scripts), it is recommended that
you add this piece of configuration also, maybe using an even larger
value.

 -- Steve McIntyre <93sam@debian.org> Sat, 23 Dec 2006 21:35:08 +0000


---

