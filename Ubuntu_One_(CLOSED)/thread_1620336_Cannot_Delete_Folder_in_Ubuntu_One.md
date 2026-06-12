---
title: "Cannot Delete Folder in Ubuntu One"
date: 2010-11-12
forum: Ubuntu One (CLOSED)
---

### Post by henrywm on 2010-11-12
I setup a backup folder in Ubuntu One with Simple Backup Config. Now the files fill my Ubuntu One account, but I cannot delete old backups or remove them from Ubuntu One. I uninstalled Simple Backup, but I still cannot remove the files. The Properties say permissions are set as root. I can delete files with the web browser interface, but then they sync back again.

---

### Post by Mia1990 on 2010-11-13
Log in as root and see if you can delete the files or folder but be very careful not to delete anything but those files or folders as you can do a  lot of damage to the os using root.


> **henrywm said:**
> I setup a backup folder in Ubuntu One with Simple Backup Config. Now the files fill my Ubuntu One account, but I cannot delete old backups or remove them from Ubuntu One. I uninstalled Simple Backup, but I still cannot remove the files. The Properties say permissions are set as root. I can delete files with the web browser interface, but then they sync back again.

---

### Post by henrywm on 2010-11-13
How do I login as root in Ubuntu? I know how to use sudo, but I cannot access the Ubuntu One folder from Terminal.

---

### Post by henrywm on 2010-11-13
I noticed that my computer is listed three times in my Ubuntu One account. I do not know why. Will deleting all instances allow me to delete the files, and will I be able to re-add my computer after that?

---

### Post by Mia1990 on 2010-11-14
> **henrywm said:**
> I noticed that my computer is listed three times in my Ubuntu One account. I do not know why. Will deleting all instances allow me to delete the files, and will I be able to re-add my computer after that?

I do not know if that will allow you to delete the files.Here is what i would try on your computer sign out of ubuntu one if it's connected then go to ubuntu one website sign in and delete any files or folders that your trying to delete from there if there is any  this will prevent them from syncing back then you can get root by typing 

> gksu nautilus and then your password this will give you root go to the folders your trying to delete and only those nothing else as you can really do damage to your ubuntu system that may cause you to need to reinstall the OS and you really don't want to do that then close out and try uploading again.

---

### Post by henrywm on 2010-11-14
I disconnected Ubuntu One in the devices tab. I also deleted the extra instances for this computer there. I do not know why there were three. Only one seemed to be in use. Anyway, your suggestion worked. Thanks.

---

