---
title: "ecryptfs on WebDAV share ... error message?"
date: 2010-01-05
forum: Security
---

### Post by schlauf on 2010-01-05
Hi everybody,

I'm trying to make ecryptfs work on my GMX Mediacenter share (a service quite popular in Germany). I followed the instructions to include my mediacenter share in my fstab which works pretty well. So now I'm able to connect via Secure WebDAV as a regular user (no sudo needed).

When connected, I try to create a ecryptfs transparent layer so everything saved remotely is seamlessly encrypted.

Although no error message is thrown during creation, the process fails. When entering the remote share (cd mediacenter) and performing any remote command such as "ls -la", the following error message is thrown:

> 
~/mediacenter$ ls
ls: cannot open directory .: Invalid argument


What's wrong here?

Thanks!

---

### Post by jeyno on 2010-09-24
bump

---

