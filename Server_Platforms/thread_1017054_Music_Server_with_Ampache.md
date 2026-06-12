---
title: "Music Server with Ampache"
date: 2008-12-20
forum: Server Platforms
---

### Post by Holmes89 on 2008-12-20
I installed Ampache today on my server and there were a few things i wanted to do in order to expand the usage.

Firstly is there a way to automatically assign permissions to files added to a folder. For example whenever I add a file to my music folder I need to go through all subfolders (all albums have their own folders) and use chmod +r /music/album/*

Secondly, I would like my friends to add songs, I have an ftp set up but I don't know how to give them accounts and have them write to the same folder and again give them permissions.

Are there any ideas? I realize that these may be simple questions but I can't seem to find an answer. Thanks in advance.

---

### Post by windependence on 2008-12-21
This may help you:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

There are several ways to do what you want to do. Probably the easiest way is to assign a default file permissions mask to a particular user on your system and have that user do all the file writes. I can't quite remember all the ways but yes there are more, and if I can find a tutorial for you I will post it here.

-Tim

---

### Post by Holmes89 on 2008-12-24
> **windependence said:**
> This may help you:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

There are several ways to do what you want to do. Probably the easiest way is to assign a default file permissions mask to a particular user on your system and have that user do all the file writes. I can't quite remember all the ways but yes there are more, and if I can find a tutorial for you I will post it here.

-Tim

That worked great, I need to figure out now how to make it give these permissions automatically when a new file is uploaded. Does anyone know how to do this? I also want to make users for an FTP server all direct to this one file and only one file, is this possible?

---

