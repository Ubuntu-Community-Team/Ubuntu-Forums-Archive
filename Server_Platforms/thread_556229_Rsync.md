---
title: "Rsync"
date: 2007-09-21
forum: Server Platforms
---

### Post by reloded on 2007-09-21
Hi guys, I need some guidance.
I want to do remote backups and I can't seem to get it all straight.

Scenario:
Ubuntu 7.04 running as file server
Windows 2003 server running Sqlserver database 

I need to backup the SQLserver database to another machine in another building via the internet.
I believe I can use backuppc to get me a copy of SQLServer database to my Ubuntu File server. But how do I get that out over the internet and into the remote machine

I've been searching around and this is what I have:
Rsync looks like the best bet.
rSnapshot -uses rsync either way

The biggest hurdle I have is directing rsync over the internet and establishing a good security mechanism.

Please assist.

Thanks

---

### Post by p_quarles on 2007-09-21
You can direct rsync connections through ssh by adding the option:
```
rsync <opts & args> -e ssh
```
The only requirement for this, of course, is that the remote machine be running an ssh server.

---

### Post by MJN on 2007-09-21
...and rsync must also be installed at the remote machine.

Mathew

---

