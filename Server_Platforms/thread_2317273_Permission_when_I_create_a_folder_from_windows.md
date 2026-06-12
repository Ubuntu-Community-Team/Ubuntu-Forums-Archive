---
title: "Permission when I create a folder from windows"
date: 2016-03-15
forum: Server Platforms
---

### Post by kambiz2 on 2016-03-15
Hi, I'm not sure if this is the correct forum, but I try.
I've shared a folder located in Ubuntu Server using Samba. When a windows user created or copy a folder, file, .... the group can only read and execute, I'd like, by default, group can read, write and execute. Is this possible?

Thanks

---

### Post by gordintoronto on 2016-03-15
Full Circle Magazine, Issue 102, page 58 might contain some useful information. It's a free download.

---

### Post by nerdtron on 2016-03-15
Add write permission for the group owner on a folder:
```
 sudo chmod g+w /shared/folder/path 
```

Also, (optionally) you may want to set the GID bit on the folder. This will cause all new files created inside that folder to inherit the group ownership of the parent folder.
```
 sudo chmod g+s /shared/folder/path 
```

more info for GID bit here: [http://www.toptip.ca/2010/03/linux-setgid-on-directory.html](http://www.toptip.ca/2010/03/linux-setgid-on-directory.html)

---

### Post by kambiz2 on 2016-03-15
Thanks for the information

---

