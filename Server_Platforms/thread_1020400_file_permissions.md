---
title: "file permissions"
date: 2008-12-24
forum: Server Platforms
---

### Post by Flance on 2008-12-24
Hello,

I have recently installed my ubuntu-server with LAMP. Then I installed vsftpd for ftp access. Now i am facing a permission problem.
My www directory is: /var/www
adding files by terminal is succesful, i get the expected permissions:
```
jordi@local:/var/www$ umask
0000
jordi@local:/var/www$ ls -l
total 8
-rw-r--r--  1 root root   20 2008-12-24 09:32 info.php
drwxr-xr-x 12 root root 4096 2008-12-24 09:52 phpmyadmin
jordi@local:/var/www$ touch a
jordi@local:/var/www$ ls -l
total 8
-rw-rw-rw-  1 jordi jordi    0 2008-12-24 10:35 a
-rw-r--r--  1 root  root    20 2008-12-24 09:32 info.php
drwxr-xr-x 12 root  root  4096 2008-12-24 09:52 phpmyadmin

```
Then, when i create a file using ftp(b):
```
jordi@local:/var/www$ ls -l
total 8
-rw-rw-rw-  1 jordi jordi    0 2008-12-24 10:35 a
-rw-------  1 jordi jordi    0 2008-12-24 10:36 b
-rw-r--r--  1 root  root    20 2008-12-24 09:32 info.php
drwxr-xr-x 12 root  root  4096 2008-12-24 09:52 phpmyadmin
jordi@local:/var/www$

```
The file permissions on b are very limited. How can I manage to automaticly make the permissions of new created files (by ftp) right?

Thanks in advance

[SIZE="1"](I'm sorry for my bad english)[/SIZE]

**Edit: solved**
I figured out there was a umask setting in /etc/vsftpd.conf, setting this from 077 to 022 fixed my problem. Thanks.

---

### Post by hyper_ch on 2008-12-24
those files should be owned by apache user "www-data"

---

### Post by RealPSL on 2008-12-24
It would help if we knew what ftp server you were using but I will assume that it is Vsftpd. There is a setting in the /etc/vsftpd.conf file that controls the upload umask of the the local users. The setting is ```
local_umask=002
```

The above will give read/write access to the user and the group. I do not recommend setting the files to world writeable. Once you have modified the /etc/vsftpd.conf you must reload or restart the ftp server with ```
/etc/init.d/vsftpd restart
```

---

