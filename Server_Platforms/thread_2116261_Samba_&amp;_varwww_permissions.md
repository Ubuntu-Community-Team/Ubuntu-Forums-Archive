---
title: "Samba &amp; /var/www permissions"
date: 2013-02-15
forum: Server Platforms
---

### Post by SAngeli on 2013-02-15
Hi,
I need help with permissions.

So far I have ubuntu server installed with samba and I can access from Windows /var/www share.
Here is what I have defined in smb.conf
```
[www]
   comment = Web Development
   path = /var/www
   browseable = yes
   read only = no
   writable = yes
   guest ok = no
   guest only = no
   valid users = @www-data
   admin users = sangeli
   max connections = 2
   create mask = 0770
   directory mask = 0770
```

On the server, I have
```
ls -la www
drwxrwxr-x  4 root www-data 4096 feb 15 15:58 www

drwxrwxr-x  4 root www-data 4096 feb 15 15:58 .
drwxr-xr-x 13 root root     4096 feb 14 20:05 ..
-rw-rw-r--  1 root www-data  177 ago 31 15:35 index.html
-rwxrwxr-x  1 root www-data   21 feb 15 13:30 info.php
drwxrwxr-x  8 root www-data 4096 feb 15 14:17 phpMyAdmin
-rw-r--r--  1 root root        0 feb 15 15:55 test
-rwxrw----  1 root sangeli     0 feb 15 15:53 test_from_windows.html
-rw-r--r--  1 root root        5 feb 15 15:58 test_from_linux.txt

```

So far I run the following commands:
```
sudo usermod -a -G www-data sangeli
sudo chgrp -R www-data /var/www
sudo chmod -R g+w /var/www
```

I need to understand permissions so that files created via Samba or via local terminal have the proper persmissions.
So far, you can notice that there are three different types of permissions assigned to the files:

-rwxrwxr-x  1 root www-data 
-rwxrw----  1 root sangeli
-rw-r--r--  1 root root

how to manage permissions? Which one is correct/shoud be for proper development?

In Samba config file share section what should I change to make sure permission will be correct?

Thank you,
Spiro

---

### Post by cj13579 on 2013-02-15
The www-data user (or user under which your HTTP server is running) only needs to have read permissions on a file to display it. So, 760 (test_from_windows.html) should be fine.

---

### Post by SAngeli on 2013-02-15
Hi,

the problem is that based on where I create the document it has different permissions.
If I create via SAMBA they are created as sangeli
If I create locally in /var/www they are created as root

Which way to go?
What should I set for chmod and chown? Is what I did ok, so far?
As for the samba share in smb.conf is it properly configured?

Thank you,
Spiro

---

