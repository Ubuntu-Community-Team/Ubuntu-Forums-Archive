---
title: "rsync problem"
date: 2006-04-08
forum: Server Platforms
---

### Post by kackland on 2006-04-08
I'm trying to backup some files in a windows 2003 share. I get a connection timeout. It's like the windows 2003 server will not let the rsync program access the share.

I can list the files with smbclient.

Do I have to do something to the windows 2003 server?

---

### Post by spanishwasabi on 2006-04-09
Windows machines do not have rsync available. So if you try to rsync to your windows server it will not work unless the admin has installed rsync by himself (don't think so...).

Enjoy,

G

---

### Post by MJN on 2006-04-09
When transferring files remotely you need to be running an instance of rsync on each machine. They then communicate with each other over TCP or via a shell (e.g. SSH etc) in order to determine between themselves what files need updating and manage the transfers accordingly (incrementally if necessary).

Thus, you need to run rsync on your Windows box - this is usually done in conjunction with cygwin - Google 'rsync windows' for plenty of HowTo's etc.

Mathew

---

### Post by baastie on 2006-04-09
Hi,

[http://www.itefix.no](http://www.itefix.no)

Has cwrsync on his site, which runs ok on 2003. He has also got copssh, for an ssh server on you windows box...

Grtz

---

