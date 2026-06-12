---
title: "How do I sync /var/www folder"
date: 2011-08-15
forum: Ubuntu One (CLOSED)
---

### Post by MuRozvi on 2011-08-15
I would like to sync my /var/www with Ubuntu one. I changed the /var/www folder permissions so to ```
drwxr-xr-x  4 murozvi murozvi 4096 2011-08-12 00:57 www
```When I right click the folder and navigate to Ubuntu One, the listed options do not highlight that I can sync the folder.

How do I get to sync the /var/www folder.

---

### Post by Dragonbite on 2011-08-16
I'm not sure, but I think UbuntuOne only sync's withing your /home directory ( or ~/).  I also don't know if it will follow symlinks either.

You could try linking the target folder into somewhere in your /home directory (maybe even as ~/Ubuntu One/www/ ?)

Like I said, I don't know if that will work or not. Let us know if it does.

---

### Post by duanedesign on 2011-08-23
Dragonbite is correct Ubuntu One will only sync within the Home directory of the user. Allowing syncing outside the Home folder opens up a large number of potential usability problem.

Also Dragonbite is right about Ubuntu ONe not following symlinks. What you can do is put the folder in the Ubuntu One folder and the symlink where the folder was.

---

### Post by keithclark on 2011-11-08
> **duanedesign said:**
> Dragonbite is correct Ubuntu One will only sync within the Home directory of the user. Allowing syncing outside the Home folder opens up a large number of potential usability problem.

Also Dragonbite is right about Ubuntu ONe not following symlinks. What you can do is put the folder in the Ubuntu One folder and the symlink where the folder was.

Thanks!  Worked out wonderful for me.

---

