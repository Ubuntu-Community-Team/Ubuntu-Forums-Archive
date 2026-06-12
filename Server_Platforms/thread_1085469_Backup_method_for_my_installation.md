---
title: "Backup method for my installation"
date: 2009-03-03
forum: Server Platforms
---

### Post by happyhacker on 2009-03-03
I use a Ubuntu server to backup all our windows PCs in the users home directories. What I need to do is backup the Ubuntu server so if I get a hardware fault or something happens that I need to reinstall and get back to the system and services I've setup so far. I do not think I need to backup the windows backups but may need to backup other users files which only exist on the server.

I have Samba, webmin, and I think Apache is installed (but not sure why).

The server has a single hdc and another drive or USB drive perhaps to perform the backups to (or maybe a windows PC which has some spare space)

I would need the backup to self run as I only visit the site once per week.

Can anyone suggest a Backup method/application?

---

### Post by Josh1 on 2009-03-03
rsync

---

