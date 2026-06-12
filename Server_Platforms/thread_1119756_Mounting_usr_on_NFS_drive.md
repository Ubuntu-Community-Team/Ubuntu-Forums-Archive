---
title: "Mounting /usr on NFS drive"
date: 2009-04-08
forum: Server Platforms
---

### Post by blingerlive on 2009-04-08
Hi All,

I'm setting up a small LAN and creating a development environment.

I was wondering if anyone has mounted their entire /usr directory using NFS so you can share all binaries and libraries on many clients. In particular, I would like all my client PCs to share gcc and all the libraries on one server to ensure everyone is developing with the same gcc and libraries.

Is this recommended? Any problems with this approach?

thanks!

---

### Post by x22 on 2009-04-08
welcome to the forum

> NFS mount /usr

good idea: I've done it w/ /etc/fstab entry

zeno:/usr   /usr  nfs  rsize=8192,wsize=8292,timeo=14,intr,noauto  0  0

you'll also need sshd

---

### Post by blingerlive on 2009-04-08
x22, I've seen on some forums that people don't recommend mounting /usr on NFS, but I don't see any major problems with doing so.

Just wondering, how many clients do you have sharing /usr on a NFS server, and what are you using it for?

---

