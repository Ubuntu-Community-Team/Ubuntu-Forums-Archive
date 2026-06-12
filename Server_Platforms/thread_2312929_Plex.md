---
title: "Plex"
date: 2016-02-08
forum: Server Platforms
---

### Post by don43 on 2016-02-08
I installed Plex on Mythbuntu,  I have two other HDD"s on the computer, both are mounted.  When I try to add folders on those drives to the Plex media library it is only allowing me to add the whole drives,  not individual folders

When I try to add the entire drive,  no files or folders are added to the library.

---

### Post by rubylaser on 2016-02-16
This sounds like it's probably a permissions issue (readable only by the root user and not the plex user).  Try chowning the files or chmoding them to more lenient permissions.

---

### Post by nerdtron on 2016-02-16
I think you can only add folders to plex and not whole drives. And as rubylaser said, try to change the ownership of the folder to plex.

```
 chown -R plex:plex /mounted/folder/plex 
```

Here's the Plex guide for permissions: [https://support.plex.tv/hc/en-us/articles/200288596-Linux-Permissions-Guide](https://support.plex.tv/hc/en-us/articles/200288596-Linux-Permissions-Guide)
The last part of the page is the Quick Guide which is quite useful.

---

### Post by ajgreeny on 2016-02-18
It may also help if you add you as user to group **plex**, and plex as user to your username group. Also make sure all files and folders on that second disk have permissions 755.

I assume the disk is formatted to an ext file system?

---

