---
title: "Ubuntu for Multiple Websites/Users with PHP and Apache"
date: 2009-06-15
forum: Server Platforms
---

### Post by rohitthakral on 2009-06-15
Setup: Ubuntu 8.10 with Apache, PHP and vsftp. Users directory used for web hosting (/home/user/website). Folder website is owned by www-data:www-data

Problem: Scripts run perfectly fine. But when I FTP with the username and password it doesn't allow me to upload any files to the directory website (Of course because the directory is owned by www-data). But this causes a lot of problems. And if I make the user the owner of the folder/files the script don't run. (It is Joomla)

Is there any easy resolution to this so that the scripts are still run properly and the upload works fine too? I have tried making the user a part of group www-data but without any success.

---

### Post by Bachstelze on 2009-06-15
Are you sure the files need to be *owned* by the www-data user? Most likely they only need to be readable by it (maybe also writable), and can be owned by any other user.

---

### Post by rohitthakral on 2009-06-15
Sorry HymnToLife,

I am not an expert. Do you mean set 756 as the permissions?

I haven't tried that as yet.

Thanks

---

### Post by Bachstelze on 2009-06-15
It depends. If the files need only be readable by the www-data user, you can sed the ownership to foo:www-data (where foo is the user whom the website belongs to), and the permissions to 750 or 755. If the files need also be writable by www-data, do the same but set the permissions to 770 or 775.

---

