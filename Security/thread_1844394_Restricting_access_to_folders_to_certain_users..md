---
title: "Restricting access to folders to certain users."
date: 2011-09-15
forum: Security
---

### Post by fenix88 on 2011-09-15
Greetings! Is there a way to restrict access to folders of non-admin users from other non-admin users, while allowing admin users to access the same folders?

---

### Post by fdrake on 2011-09-15
> **fenix88 said:**
> Greetings! Is there a way to restrict access to folders of non-admin users from other non-admin users, while allowing admin users to access the same folders?

you can change the permission of the file/folder
```
sudo chmod 770 -R /home/user/Desktop/my_folder
```
this command will make the folder(and its current files readable/writable/executable to only the owner user and the members of its groups)
to change group of a file/folder (to the admin group)
```
sudo chgrp -R admin /home/user/Desktop/my_folder
```

to view the permissions of a file/folder do:
```

ls -al /home/user/Desktop/my_folder

```
for more info google around "linux permissions" ([http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml))
note: if you create new files the opermissions may be different depending on your umask!

---

### Post by fenix88 on 2011-09-15
All right! Thanks!

Is it safe to implement the chgrp in /etc/profile

---

### Post by Morbius1 on 2011-09-15
My only caution to what was posted above concerns this line:
> sudo chmod 770 -R /home/user/Desktop/my_folderThat will make every directory executable which you must do but it will also make every file executable which you probably don't want to do. Octal mode chmod can't differentiate between a folder and a file so I would suggest doing it this way:
```
 sudo chmod -R a+rwX,o-rwx /home/user/Desktop/my_folder
```The big "X" makes folders executable, keeps files that are already executable alone, and doesn't make non-executable files executable.

---

