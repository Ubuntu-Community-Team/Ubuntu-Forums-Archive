---
title: "Accessing Ubuntu server resources remotely via Samba"
date: 2013-01-30
forum: Server Platforms
---

### Post by SAngeli on 2013-01-30
Hi,
I have an ubuntu server set for NAS and web development tasks in my LAN.
I use Windows 7 for my daily IT activities and wish to access some server resources mapping to windows network shares so that they appear on my PC as a drive with a letter assigned (ex: h:\)
I also use Samba do do so.

**Q.A** I need help in properly understanding setting directory permissions.

How to be able to rwx root data? I did not find any wheel group in ubuntu, thoguh I am also in admin group. I wish to avoid chmod 777 as it would become unsafe.

These is where I am added to:
```
adm:x:4:sangeli
cdrom:x:24:sangeli
sudo:x:27:sangeli
dip:x:30:sangeli
plugdev:x:46:sangeli
sambashare:x:116:sangeli
sangeli:x:1000:
lpadmin:x:118:sangeli
nas:x:1002:sangeli
```

These are the directories I wish to network map:
- /var/log Current permission: drwxr-xr-x 18 root root 
- /var/www Current permission: drwxr-xr-x 18 root root 

If I change (-R) group and leave ownership to root whould I create any malfunction to ubuntu server?

***Note**: I also tried using admin users = sangeli but it did not work. Perhaps I used it incorrectly? This should have been the solution to my question.No?*

**Q.B** If I wish to also access to these files via ftp what do I need to install and configure to access them too (so I simulate I connect as I would do with my ISP web Hosting)?.

Thank you,
Spiro

---

### Post by SeijiSensei on 2013-01-30
> **SAngeli said:**
> These are the directories I wish to network map:
- /var/log Current permission: drwxr-xr-x 18 root root 
- /var/www Current permission: drwxr-xr-x 18 root root 


Take a look at the Samba directives "force user" and "force group".  I've used the first to share out a website directory to Windows users.  They connect with their own user ids, but the files are written as, in my case, user "web", which owns the website directories on their server.  (I set the DirectoryRoot to /home/web/public, owned by user and group "web", and export the share as "[website]" with Samba.)

---

