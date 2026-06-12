---
title: "Backup server"
date: 2005-02-17
forum: Server Platforms
---

### Post by SadnesS on 2005-02-17
Hello.

I need to know how i can solve this little problem. I wan't build backup server. Clients connect on they Window$ to my Ubuntu server and they can upload her/hes files, but can't delete it. And each client has own drive, example, John has Windows XP and he wan't backup his Word documents to backup server. He goes on My Computer and click drivename (example H) and he can copy/paste files on it. 

How i can do this? I know, i need use Samba and maybe FTP, but whats is best way to solve this. 

This is easy solve with Windows 2000/2003 servers, but micro$oft....    :roll:

---

### Post by nemin on 2005-02-17
[QUOTE=SadnesS]Hello.

I need to know how i can solve this little problem. I wan't build backup server. Clients connect on they Window$ to my Ubuntu server and they can upload her/hes files, but can't delete it. And each client has own drive, example, John has Windows XP and he wan't backup his Word documents to backup server. He goes on My Computer and click drivename (example H) and he can copy/paste files on it. 

How i can do this? I know, i need use Samba and maybe FTP, but whats is best way to solve this. [/QUOTE]
I think samba would be the best way to do this, you can compare it very well with windows' file sharing capabilities. Things like file permissions, you can all configure with samba. Good place to start is [www.ubuntulinux.org/wiki/SettingUpSamba](www.ubuntulinux.org/wiki/SettingUpSamba) I guess. Good luck.

---

