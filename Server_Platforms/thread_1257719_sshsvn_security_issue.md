---
title: "ssh/svn security issue"
date: 2009-09-04
forum: Server Platforms
---

### Post by artheus on 2009-09-04
Hi!

I've recently installed an svn-repository on my ubuntu 9.04 server. And that requires that I use an svn+ssh protocol. Which means that I'd have to open the ssh port for my server to the www. And I don't really want that. So either, I'd want to config the ssh so that it doesn't let any ssh client connect to it, or sftp, which is a big security issue.
I'd really just want to either disable the sftp feature of ssh, or just change the protocol of my svn.

How?

I'm using Openssh, and subversion.

Cheers,
Artheus

---

### Post by hessiess on 2009-09-04
Use Apache with mod_dav_svn and TLS(SSL) instead.

---

### Post by artheus on 2009-09-05
Thanks!

Are there any good tutorials to do this? I can't seem to find any.. I find a partial How-to.. but no good one..

Cheers,
Artheus

---

### Post by jay.parnaby on 2009-09-05
Try this one

[Installing Subversion on a Home Ubuntu Server]("http://www.keithscode.info/index.php?option=com_content&view=article&id=27%3Asubversion&catid=18%3Alinux-tutorials&Itemid=34&showall=1")

---

### Post by artheus on 2009-09-06
Really great! Works like a charm! Thanks a lot!

Cheers,
Artheus

---

