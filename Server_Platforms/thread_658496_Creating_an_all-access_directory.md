---
title: "Creating an all-access directory"
date: 2008-01-04
forum: Server Platforms
---

### Post by vsiege on 2008-01-04
I want to set up a directory so that all users of a particular group have all access rwx. Is this possible?
I read up on umask but that didnt seem to work. I logged into each user and went to terminal, then typed ```
umask 002
```, but when i create a file it just keeps read-only for the group.
basically it would be nice if any user of a group could save there work to the directory and already have thre correct permissions on the newly created file. I do not want to use cron for this.

---

### Post by WearZeeP on 2008-01-04
Doesn't
> chmod g+rwx -R yourdirectory/*
work?

---

### Post by vsiege on 2008-01-06
I used the commands as you suggested under one of the user accounts like such in the terminal:```
sudo chmod g+rwx -R /media/best2/*
``` then checked the files & folders that were already in the directory but the permissions were still the same. I created new files in the directory and the group still only had read permissions.

---

