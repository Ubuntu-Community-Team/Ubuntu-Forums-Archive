---
title: "Clients with folder"
date: 2013-07-31
forum: Server Platforms
---

### Post by PaulNL on 2013-07-31
Hello All, I have setup a OpenVPN server and all works perfect but..... in the past i had a server where i had folders with the name of the user who is permitted to access the server.

the trick was to make a folder in the same name as his Key.

The problem is i don't know how i did it. someone a idea ??

Paul

---

### Post by TheFu on 2013-07-31
What client and which server are involved?
Users on Linux normally have a HOME ... something like /home/pete where all their personal files are stored.
If you want a group of users to share files, then you might create a directory, something like .... /data/group_files/ and set the file/directory permissions for the files AND on the user accounts so that every user gets either read-only or read-write permissions as needed.

If you are using CIFS/Samba as the file access method, there are lots of bute-force solutions that lose the subtle intricacies provided by straight Linux file system permissions.

Lots of ways to accomplish this, we just need more information about your setup.

---

