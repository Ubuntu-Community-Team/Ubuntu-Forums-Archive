---
title: "sshfs &amp; fstab =&gt; system hangs?"
date: 2018-01-07
forum: Server Platforms
---

### Post by gary64 on 2018-01-07
Hi there,

still trying to mount an HFS volume permanently. But now, the system hangs after reboot after I inserted this line in /etc/fstab

```
sshfs#admin@remote.host:/Volumes/Incoming/ukrdc /home/master/gcc

```

I completely re-installed the whole server 16.04.03, installed only sshfs (and nothing else). Everything is out of the box. Mounting is successful in shell session with:

```
sshfs -o allow_other,idmap=user,IdentityFile=~/.ssh/id_rsa admin@remote.host:/Volumes/Incoming/ukrdc /home/master/gcc/

```

Any ideas?

Thanks!

---

### Post by TheFu on 2018-01-07
I've attempted to get sshfs to mount in the fstab and always failed. This was between Ubuntu systems.  I don't think it works.

YMMV.

---

### Post by Max303 on 2018-01-11
Assuming the passwordless auth works for that admin user, and you have the "fuse" pkg installed, this should also work in fstab:

sshfs#admin@remote.host:/Volumes/Incoming/ukrdc /home/master/gcc fuse defaults,allow_other 0 0

---

