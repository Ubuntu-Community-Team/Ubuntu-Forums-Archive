---
title: "users without home diretory - login folder"
date: 2008-01-20
forum: Server Platforms
---

### Post by orszagh on 2008-01-20
Hi,

I have several users on server that have no home directory (they do not need it), but all of them are using files in one common directory (e.g. /var/docs ). These users log in just through SFTP. Is there a way how these users could be automatically (after login) moved to the directory they need ( /var/docs ) and not to the root directory? (When loging in through SFTP)

Thank you very much.

---

### Post by fimblo on 2008-01-28
how bout setting their home directory to /var/docs?

---

