---
title: "MySQL in chroot gaol won't stop"
date: 2010-12-08
forum: Server Platforms
---

### Post by leojfc on 2010-12-08
Hello,

I am running 8.04 on a remote server, with three separately chrooted LAMP servers running on it, listening on different ports.

The MySQL servers, one per chroot, now refuse to restart or stop.  I can't find anything in syslog or the various mysql logs giving a reason, it just fails as follows:

```
sudo schroot -c testserver -u root -d "/root" -- /etc/init.d/mysql stop
I: [testserver chroot] Running command: “/etc/init.d/mysql stop”
 * Stopping MySQL database server mysqld
   ...fail!

```

Has this happened to anyone else?  Can anyone suggest anywhere else I could look for information or tests I could use to diagnose better?

Many thanks in advance,

Leo

---

