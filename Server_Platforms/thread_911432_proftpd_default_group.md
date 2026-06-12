---
title: "proftpd default group"
date: 2008-09-05
forum: Server Platforms
---

### Post by guilly on 2008-09-05
Hi guy's,

I'm trying to set up a specific directory on my ftp server so that when a user uploads a file the permissions get set so that the user is the owner of the file but the group is not the user.

for example if user X uploads something I want the ownership to be something like x:y and not x:x. Where x is the users name?

is this at all possible?

I looked into the Umask however i think that is geared more towards the permissions if Im not mistaken.

thanks

---

