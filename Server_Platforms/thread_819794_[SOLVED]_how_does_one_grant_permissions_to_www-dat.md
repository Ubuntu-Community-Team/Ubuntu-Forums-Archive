---
title: "[SOLVED] how does one grant permissions to www-data?"
date: 2008-06-05
forum: Server Platforms
---

### Post by brook adams on 2008-06-05
Hi There,

I'm running apache2 with a php5 module and I want to save a file to a folder. 
apache appears to be running as the user www-data. How do I grant permissions to www-data to save stuff in a particular folder?

I tried the GUI users and groups utility but it shows no user www-data unless I try to add one and then it says this user already exists... I looked in the  /etc/group file and found a group by that name but I thing I'm looking for a way to assign the user www-data membership in the group which owns the folder(s) in question... Right?

Thanks in Advance...

---

### Post by turinglabs on 2008-06-05
You want the chgrp command to change the group ownership on the directory in question, and the chmod command to change the permissions so that the group www-data has read, write and execute permissions on the directory. Say the directory you want to save files in is /var/www/files, then from a shell prompt:

```

cd /var/www
sudo chgrp www-data files
sudo chmod g+rwx files

```

---

