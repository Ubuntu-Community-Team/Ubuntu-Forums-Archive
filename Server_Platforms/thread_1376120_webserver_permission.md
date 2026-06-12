---
title: "webserver permission"
date: 2010-01-08
forum: Server Platforms
---

### Post by fouadk on 2010-01-08
hi everyone...

im running an apache webserver and using virtual hosting...the folders are located in /var/www...

one of my virtual hosts have chown permission set to root:www-data with chmod 775...

the page is a php script that creats some folders in /home/user/files/desktops and change chown and chmod using linus built in chown and chmod using php exec function...the username are get from winbind...

this script have been working flawlessly for 1 year...yesterday something went wrong and the script cannot change to proper ownership newly created folders...so the newly created folder are with root:root ownership where they should be sampleuser:domain admins instead for example...chmod is working but not chown...

im running ubuntu server 8.04.3...the script worked like a charm for more than a year so i know its doable and it works...as mentioned above, the script permission are root:www-data and www-data is added to the sudoers...

i have no idea how to debug this one...please help and thanks in advance

---

### Post by Vegan on 2010-01-08
you can make a symbolic link into your web root folder but make sure the permissions are set properly.

---

### Post by fouadk on 2010-01-09
you mean i should make a symbolic link of my /home/user/files/desktop in /var/www ????

what should be the permissions of the symbolic link so it is secure ????

---

### Post by BkkBonanza on 2010-01-09
There must be some reason this has changed yesterday. Was something updated? Perhaps PHP got updated and a new php.ini replaced what was there before? If php.ini changed then some security settings may be different. In general php should not be able to run a shell that has root access needed to chown. The fact that it did would imply that some non-standard safety setting was in place which now may have been reverted to the default.

Anyway, this is what comes to mind without knowing more about how you've configured things.

---

### Post by fouadk on 2010-01-09
php installation was a standard one...i installed the LAMP package that you get when u first install ubuntu server....

the only thing i added is add www-data to the sudoers files...

what can possibly go wrong ?

---

### Post by fouadk on 2010-01-09
this was solved by a simple restart :D

---

