---
title: "Change file permissions"
date: 2010-08-28
forum: Server Platforms
---

### Post by JD32 on 2010-08-28
So i pulled some files off my buddy's computer via my wireless home network, i can access them but in the permission tab the owner is "nobody" so i can move the files. How can i change the permissions to enable me to move the files?

---

### Post by minigeek on 2010-08-28
> **JD32 said:**
> So i pulled some files off my buddy's computer via my wireless home network, i can access them but in the permission tab the owner is "nobody" so i can move the files. How can i change the permissions to enable me to move the files?

Hi 

Use the chown command from the command line.

Change to the location of the files and run the following

chown yourname:yourgroup filename

Or right click on the file and choose properties the permissions and change the owner of the file to ypurself

This will make you the owner of the files

:)

---

### Post by JD32 on 2010-08-28
sorry im new to linux and command line, How exactly do i run that?

---

### Post by minigeek on 2010-08-28
> **JD32 said:**
> sorry im new to linux and command line, How exactly do i run that?

Hi

From the menu choose Applications>Accessories>Terminal

This will open the default terminal

at the command prompt enter the following

```
sudo chown yourname:yourgroup filename
```
:D

---

