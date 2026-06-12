---
title: "Samba &amp; file permission"
date: 2013-08-07
forum: Server Platforms
---

### Post by netum on 2013-08-07
Good day.
There is a server Ubuntu 12.04 - Samba file server. Part of the config for shared folders
```
[Qwe]
    read only = no
    path = /mnt/qwe
    guest ok = yes
    browseable = yes
```
The rest of the config all in default.
There is a folder tree
[LIST]
[*]qwe (755 root @ root)
[LIST]
[*][*]asd (755 root @ root)
[LIST]
[*][*][*]1 (777 root @ root)
[*][*][*]2 (777 root @ root)
[*][*][*]3 (777 root @ root)
[*]
[/LIST]
[/LIST]
[/LIST]
The idea is this: users can create files and folders only in the digital folder (1,2,3). In "qwe" and "asd" on the record, renaming, and deleting closed rights (755).
In reality, the situation is not simple. In digital, you can create folders or files and delete - that's fine. If you go up one level in the folder "asd" containing digital files and try to remove one of them:
in Windows XP - deleted without question, a digital folder and all its contents. Click in Explorer update and miracle appears with the same name as the folder, but it is empty.
in kUbunte 13.04 - "Dolphin" swears that the folder "smb://server/qwe/asd/ (here the name of the deleted digital folder) is forbidden." BUT if you click refresh and go to that folder, it is empty.
In this case, the server I see that created and deleted immediately available navels changing, as in the removal through Windows, and kUbuntu.
A task such as simple. It creates a folder tree with the opening of network access to the very top and permission to write and modify only the lowest directories. Without the ability to delete or rename these lower directory.
Can you please tell how to solve this problem?

---

