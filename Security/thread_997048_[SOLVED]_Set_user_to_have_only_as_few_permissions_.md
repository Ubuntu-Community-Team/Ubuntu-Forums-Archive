---
title: "[SOLVED] Set user to have only as few permissions as possible"
date: 2008-11-29
forum: Security
---

### Post by abcuser on 2008-11-29
Hi,
on Ubuntu 8.10 I would like to create a new user to have as low priority as possible. I would like new user could run programs and save files to his home directory and to have access to web sites. I don't want this user to have any kind of installation option.

Just something like Users group on Windows XP which all users in this group doesn't have any system rights (installing, configuring etc).
Regards,
Abcuser

---

### Post by .nedberg on 2008-11-29
If you create a new user that would be the default.

The first user is an administrator with sudo rights and can install programs, change config files.

The next users will default to "normal" users without these rights, unless you give them that right.

---

### Post by lswb on 2008-11-29
When a new user is added by default he/she will not have admin priveledges. You can fine-tune this to some extent from Main Menu/System/Administration/Users and Groups. Click on "unlock" and enter password. Then add a user or select an existing user and click on Properties. Under the "User Priveledges" tab you can allow/restrict various capabilities for the user. Under the "advanced" tab you can also change the shell for the user to rbash but that is needlessly cruel IMHO.

---

