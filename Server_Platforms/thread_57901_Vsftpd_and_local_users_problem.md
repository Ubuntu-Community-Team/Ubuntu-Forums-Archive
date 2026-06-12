---
title: "Vsftpd and local users problem"
date: 2005-08-18
forum: Server Platforms
---

### Post by mad_archer on 2005-08-18
I have managed to set up vsftpd to allow ftp access to all my local users.  However I want to try to prevent these users from all logins except for ftp when they are chrooted to their home dirs

I have tried to edit /etc/passwd and have tried to assign shells such as /dev/null /bin/false /bin/true /sbin/nologin so as to prevent logons.  Unfortunately I seem only to be able to connect if the shell is /bin/bash and therefore i can also login via ssh and locally.

Any ideas on how to fix this?

John

---

