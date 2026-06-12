---
title: "Can't ssh to server with root account because of gitosis"
date: 2010-12-28
forum: Server Platforms
---

### Post by tranduyhung on 2010-12-28
Hi!

This is the error message:

> username@hostname:~$ ssh root@192.168.1.1
PTY allocation request failed on channel 0
ERROR:gitosis.app:Configuration does not exist: [Errno 2] No such file or directory: '/root/.gitosis.conf'
192.168.1.1 closed.I installs gitosis and now it works well, but I realize that I can't ssh with root user becasue of this problem. I can still login via ssh with other user accounts and use sudo to manage server.

How could I fix this problem?

Thank you!

All the best,
Hung

--------------------------------------------------

I fixed it!!
Just remove /root/.ssh/authorized_keys :D.**

---

