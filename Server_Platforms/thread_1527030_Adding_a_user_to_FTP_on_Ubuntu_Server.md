---
title: "Adding a user to FTP on Ubuntu Server?"
date: 2010-07-08
forum: Server Platforms
---

### Post by davetelex on 2010-07-08
I have googled around a bit but i keep getting different results. I want to add a new user to my FTP server. Im not entirely sure what ftp server im using. When i set up my server i used this site: [http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/) .  It seems when i set up the server originally my admin username seems to be added to the ftp server as well. Now i want to have a new user on my server. That user can ssh into the server but when they use filezilla to ftp they can only download in it and not upload. So im assuming that they need permissions somewhere which im assuming is somehow adding them to the ftp server. I am brand new to Ubuntu and Ubuntu server, please help!

---

### Post by doogy2004 on 2010-07-08
The tutorial you linked states that you are using SFTP not FTP.

> Now, you’re going to log into your server using SFTP (not to be confused with FTPS).

In your FTP client, there should be a box for Port.  Set the port to 22.

---

### Post by Vegan on 2010-07-08
vsftp is the best choice for Ubuntu as it is easy to setup anyway you want

```
sudo apt-get install vsftp
```

---

### Post by davetelex on 2010-07-08
I would prefer to stay with whatever ftp server i have now, i just want to add another user that has the same access privileges that i have. and 22 is put in the port box on the client and it will connect to the server for both of us. Only difference is for me i can upload and download and for him he can only download. That is what im trying to fix. If it comes down to it i am willing to change my ftp server, i would prefer to stick with the one i have now though.

---

### Post by doogy2004 on 2010-07-11
What folder is your second user attempting to upload to?

---

### Post by davetelex on 2010-07-13
The location of the rest of the served files on the server: /var/www/ the same place that im accessing

---

### Post by doogy2004 on 2010-07-13
> **davetelex said:**
> The location of the rest of the served files on the server: /var/www/ the same place that im accessing

you will need to change the permissions of that folder to allow the other user to write to it.

what is the output of this command?

```
ls -al /var/www/
```

---

### Post by davetelex on 2010-07-14
total 184
drwxrwxr-x  7 www-data www-data  4096 2010-07-08 19:17 .
drwxr-xr-x 15 root     root      4096 2010-06-17 14:35 ..
-rw-r--r--  1 dave     www-data  7462 2010-07-12 22:36 about.html
drwxr-xr-x  3 dave     www-data  4096 2010-07-08 15:51 dev
-rw-r--r--  1 dave     www-data  7019 2010-07-08 17:30 dthosting.html
-rw-r--r--  1 dave     www-data  5383 2010-07-08 17:30 empty.html
drwxr-xr-x  2 dave     www-data  4096 2010-07-08 19:17 files
drwxr-xr-x  2 dave     www-data  4096 2010-07-07 18:07 game
-rw-r--r--  1 dave     www-data  6934 2010-07-14 12:19 games.html
drwxr-xr-x  2 dave     www-data  4096 2010-07-06 18:11 images
-rwxrwxr-x  1 www-data www-data  5429 2010-07-08 17:43 index.html
-rw-r--r--  1 dave     www-data 10893 2010-07-08 17:30 probsubmit.html
-rw-r--r--  1 dave     www-data 10339 2010-07-08 17:30 probsubmitt.html
drwxr-xr-x  2 dave     www-data  4096 2010-06-30 17:49 pw
-rw-r--r--  1 dave     www-data  5965 2010-07-08 17:30 quests.html
-rw-r--r--  1 dave     www-data  6601 2010-07-13 15:43 scouts.html
-rw-r--r--  1 root     root     16771 2010-07-08 18:31 search.html
-rw-r--r--  1 dave     www-data    61 2010-07-08 17:30 sitehelp.html
-rw-r--r--  1 root     root      2438 2010-07-08 17:41 sitemap.xml
-rw-r--r--  1 dave     www-data  1535 2010-07-08 17:30 tabcontent.css
-rw-r--r--  1 dave     www-data  9025 2010-07-08 17:30 tabcontent.js
-rw-r--r--  1 dave     www-data  4240 2010-07-08 17:30 templatemo_style.css
-rw-r--r--  1 dave     www-data   206 2010-07-09 00:14 test.html
-rw-r--r--  1 dave     www-data  7421 2010-07-13 17:20 update.html
-rw-r--r--  1 dave     www-data  8721 2010-07-12 22:36 wsites.html

---

### Post by doogy2004 on 2010-07-14
> **davetelex said:**
> drwxrwxr-x  7 www-data www-data  4096 2010-07-08 19:17 .
drwxr-xr-x 15 root     root      4096 2010-06-17 14:35 ..

Notice the two lines at the top.  The first one (.) shows you the permissions for the current folder.  The second one (..) shows you the permissions for the parent directory.  Column 1 is the read, write, execute permissions. Column 3 is the owner, and Column 4 is the Group.  There are many resources that explain this in more detail.  For the second user to be able to write to the directory you need to add them to the www-data group.  Use the following command to add the user to the www-data group:

```
useradd -G www-data username
```

Resources:
Google search for Linux Permisions - [https://encrypted.google.com/search?q=linux+permissions](https://encrypted.google.com/search?q=linux+permissions)
MAN page for useradd - [http://ss64.com/bash/useradd.html](http://ss64.com/bash/useradd.html)

---

