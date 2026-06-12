---
title: "File System Structure for FTP"
date: 2010-11-10
forum: Server Platforms
---

### Post by matthew.parlette on 2010-11-10
I'm in the process of setting up an Ubuntu server to replace the 5 crappy Windows servers that I was left to manage for my small company.

Right now I'm setting up the FTP server, but before I do, I want to get some opinions on the best way to structure my file system.

For FTP shares, should I create a /var/ftp folder to store it, or /usr/ftp, or /usr/share/ftp?

I'd like to have these FTP files shared over Samba to the local network, but I'm really trying to decide on putting it in /usr or /var, or maybe what the general admin population does in this case.

---

### Post by matthew.parlette on 2010-11-12
In case anyone has the same question and stumbles onto this post, I looked here:
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html)

This page points to creating /home/ftp, so what I'll do is create a few folders under /home to share over samba and ftp

---

