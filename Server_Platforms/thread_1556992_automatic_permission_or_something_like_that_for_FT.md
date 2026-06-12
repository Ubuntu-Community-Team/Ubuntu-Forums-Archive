---
title: "automatic permission or something like that for FTP"
date: 2010-08-20
forum: Server Platforms
---

### Post by Project_Pat on 2010-08-20
so i just FINALLY got my ftp samba and all that stuff working because of permission stuff... but the problem i find is that every time i upload something to my apache web server, it has no read access for new files and i have to put the read permission manually. Is there any way i can set it so all files in that directory have read attribute automatically? Ive looked up things and i see umasks but i don't know how to use it if that's my solution

---

### Post by Ryan Dwyer on 2010-08-20
Is your Apache DocumentRoot /var/www or did you change it to somewhere in your home directory? If you left it as /var/www, you must have changed the permissions so your account can put files there using FTP.

Where ever it is, you can probably fix it by making www-data a member of your group and making sure the group has read access on those files.

---

### Post by Project_Pat on 2010-08-20
nonno cuz when i dont have read access on it no one can see it as in the public. for it to work i have to manually put the permission in. the path is still /var/www/. yea i opened up permission so that i could put files there but when i put, lets say a new pictures, it starts off with teh permisssions -rw------- and no one other than me (creatior) can see it.

---

### Post by Project_Pat on 2010-08-21
bump?

---

### Post by Bachstelze on 2010-08-21
Look at local_umask in your vsftpd.conf.

---

### Post by Project_Pat on 2010-08-21
YES!! THANK YOU!!!!!!
for other people...the mask 022 sets it to -rw-r--r-- so EVERYONE can read it YAYAYAYAY thanks ^^

---

