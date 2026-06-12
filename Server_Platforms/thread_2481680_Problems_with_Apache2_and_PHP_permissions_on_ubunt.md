---
title: "Problems with Apache2 and PHP permissions on ubuntu 20"
date: 2022-12-06
forum: Server Platforms
---

### Post by gatoher on 2022-12-06
Hello everyone I can't give proper permissions to Apache2 in Ubuntu 20. Every time a directory is created or a photo is uploaded to the server the owner is the user www-data who has all the permissions. But the rest of the group of which I am a member can only access the files.  The permissions remain as seen by the console:

**drwxr-sr-x   2 www-data www-data 4096 nov 30 20:18 72**


I have followed several ways on the internet. They work for me but only for the files already created, 
every time I follow the steps of several forum posts, 
my user recovers the permissions to delete the images or files uploaded. 
But as soon as a new one is created, we return to the same ones, only the www-data user can delete them, etc.

---

### Post by pqwoerituytrueiwoq on 2022-12-06
what i do is make a folder for data saved by www-data
```
mkdir /var/www/html/data
sudo chown www-data:www-data /var/www/html/data
```

www-data can read/write/delete anything inside this folder

it probably can delete the folder itself but it will not be able to make it

---

