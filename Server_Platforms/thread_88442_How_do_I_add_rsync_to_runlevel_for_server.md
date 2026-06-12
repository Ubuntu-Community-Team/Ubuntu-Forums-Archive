---
title: "How do I add rsync to runlevel for server?"
date: 2005-11-10
forum: Server Platforms
---

### Post by Stephen-I-M on 2005-11-10
I see that one of the rsync packages puts a script in /etc/init.d.

How do I add it to a runlevel so that it starts up when the computer is rebooted?

[edit] I see a rsyncd.conf here:

$ locate rsyncd.conf
/usr/share/doc/rsync/examples/rsyncd.conf
/usr/share/man/man5/rsyncd.conf.5.gz

but it isn't installed in /etc anywhere. Is this a bug?

Stephen

---

### Post by LordHunter317 on 2005-11-10
No, the file is there, your locate database is out of date.

You use update-rc.d.  THe default runlevel is 2.  It was probably added automatically and you need to change /etc/default/rsync[d] to get it to work.

---

