---
title: "RECYCLER VIrus in my Ubuntu"
date: 2008-12-10
forum: Security
---

### Post by JorgeMIlla08 on 2008-12-10
I know this famous RECYCLER virus is windows only, i remember trying to delete it from windows before i started using ubuntu, anyway a friend ask me to copy him a game i had for windows, he let me his USB drive, so when I opened the drive i noticed the infamous RECYCLER folder, i was about to  deleting it permanently with shift + Del when it tells me I dont have the necesary permisions to delete the file, a FOLDER made on windows with windows executables had read only permisions? i tried to change the permisions through file properties but still nothing...

This just questions the posibilyty of a linux virus, the kind of virus you cant delete without comand lines scipts etc...

I tough ubuntu didnt take the windows permisions in consideration when overwriting fat USB
This should be fixed if its considered a bug, souldnt everything in a windows format be overwritable from Ubuntu.
Any ideas on how to clean this USB? Please

---

### Post by Sarmacid on 2008-12-10
I've never had problems removing this folder from the console. Don't even need to chmod, just the good old ```
sudo rm -r RECYCLER
``` and it's done.

---

### Post by bodhi.zazen on 2008-12-10
chmod will not work on FAT/NTFS file systems as you set permissions when you mount.

```
sudo rm -rf /path/to/RECYCLER
```

---

### Post by Sarmacid on 2008-12-10
Yes! sorry, typed chmod thinking of rm :mad:

---

### Post by JorgeMIlla08 on 2008-12-11
Great thanks! but still its weird that i couldnt remove such folder with the "del" key as it says i dont have the privileges to do so, from a FAT USB, ?

Btw the sudo rm -rf /media/(USB NAME)/RECYCLER fixed it, but still I am curious about this FAT/NTFS read-only privileges for windows executables in ubuntu.

---

### Post by bodhi.zazen on 2008-12-11
> **JorgeMIlla08 said:**
> Great thanks! but still its weird that i couldnt remove such folder with the "del" key as it says i dont have the privileges to do so, from a FAT USB, ?

Btw the sudo rm -rf /media/(USB NAME)/RECYCLER fixed it, but still I am curious about this FAT/NTFS read-only privileges for windows executables in ubuntu.

If you are interested, see this link : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

Or there is always man mount

Basically FAT/NTFS file systems do not support permissions, so part of mounting is setting permissions.

You can set permissions with umask, fmask, and dmask.

---

