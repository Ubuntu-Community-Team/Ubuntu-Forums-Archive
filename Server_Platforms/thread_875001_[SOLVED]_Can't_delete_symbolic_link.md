---
title: "[SOLVED] Can't delete symbolic link"
date: 2008-07-30
forum: Server Platforms
---

### Post by samona on 2008-07-30
hi all,

I'm trying to delete a symbolic link.  Unfortunately it is linked to the folder it resides in.  When i try to delete i get the following 

```

user@server:/usr/share/phpmyadmin$ rm phpmyadmin -> phpmyadmin
-bash: phpmyadmin: Too many levels of symbolic links
```


Does anyone know what I must do to remove it successfully without having to delete the whole folder?  Thx!

---

### Post by k_grdn on 2008-07-30
Hi,


You can just delete the link and not the source folder with rm, also I suggest moving to a non-related dir.


Regards,

k_grdn

---

### Post by Dr Small on 2008-07-30
Try:
```
sudo unlink filename
```

---

### Post by samona on 2008-07-31
Thanks guys.  the unlink command worked.  I dunno why the rm didnt.

---

