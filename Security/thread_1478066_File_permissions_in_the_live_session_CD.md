---
title: "File permissions in the live session CD"
date: 2010-05-09
forum: Security
---

### Post by diddybones on 2010-05-09
I  have broken my MBR and can now only enter 9.10 with the ubuntu start up  cd.

when i boot through he ubuntu live cd

I can see my mounted drive with all my files however i do not have the permissions to open or copy some of my files( music, films, pics) . id like to do this so i can transfer all my files to an  external HDD and reformat start all over again

error when trying to open files


**You do not have the permissions necessary to view the contents of .....**

How can i get around this issue

---

### Post by cariboo on 2010-05-09
This isn't really a security question. To answer it, just preface your command with sudo, for example if you want to use the file manager to transfer files between drives, press Alt-F2 and type:

```
gksu nautilus
```

You won't be asked for a password. The above command opens the file manager (nautilus) as root, allowing you to move files between drives you don't have permissions to as a normal user.

---

