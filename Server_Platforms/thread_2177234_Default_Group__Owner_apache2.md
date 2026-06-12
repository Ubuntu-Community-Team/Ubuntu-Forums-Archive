---
title: "Default Group / Owner apache2"
date: 2013-09-27
forum: Server Platforms
---

### Post by alfirdaous on 2013-09-27
Hello everybody,

I created a user by the name "alfirdaous", I made a site under sites-available by the same name "alfirdaous", while executing a command line using apache2, something like:

[PHP]
$cmd = "/usr/bin/ffmpeg -f mp3 .... FileName.mp3";
$execute = exec($cmd);
[/PHP]

The file is created with the Group / Owner www-data, how can I make it by default to be created with the username "alfirdaous"

Thanks in advance

---

### Post by CharlesA on 2013-09-27
Read this:
[http://askubuntu.com/questions/97810/how-to-make-apache-run-as-current-user](http://askubuntu.com/questions/97810/how-to-make-apache-run-as-current-user)

Just add your user to the www-data group and you will be able to access the file.

---

### Post by alfirdaous on 2013-09-27
Thanks for the link:

this is the result:

```

PHP Warning:  fopen(file.txt): failed to open stream: Permission denied in /home/alfirdaous/www/newFile.php on line 3

-rw-r--r-- 1 alfirdaous alfirdaous 3 Sep 28 02:33 file.txt

# getent group www-data
www-data:x:33:alfirdaous


```

by doing this simple script:

[PHP]
<?php
$my_file = 'file.txt';
$handle = fopen($my_file, 'w') or die('Cannot open file:  '.$my_file); //implicitly creates file
?>
[/PHP]

so the file was not created and generated the above error

---

### Post by CharlesA on 2013-09-27
Double check the permissions for the entire directory tree to make sure the permissions are correct.

```
ls -ld /home
ls -ld /home/alfirdaous
ls -ld /home/alfirdaous/www/

```

You might also have some lucky checking the logs for apache.

---

### Post by sandyd on 2013-09-28
> **alfirdaous said:**
> Thanks for the link:

this is the result:

```

PHP Warning:  fopen(file.txt): failed to open stream: Permission denied in /home/alfirdaous/www/newFile.php on line 3

-rw-r--r-- 1 alfirdaous alfirdaous 3 Sep 28 02:33 file.txt

# getent group www-data
www-data:x:33:alfirdaous


```

by doing this simple script:

[PHP]
<?php
$my_file = 'file.txt';
$handle = fopen($my_file, 'w') or die('Cannot open file:  '.$my_file); //implicitly creates file
?>
[/PHP]

so the file was not created and generated the above error
Change to the www-data user
```
su www-data
```
start at the root directory and start browsing up until you find the permission denied error
Then you can change the permissions on that directory

If your really bored, check out mod_ruid2 - which changes the user on the apache2 threads to the one you specify in the virtual hosts - then basically, everything created by php scripts or html upload/etc will be owned by the user

---

### Post by alfirdaous on 2013-09-30
this is the result:

newFile.php is the file where the script it coded

```

root@SERVER:/home/desktop# ls -ld /home/
drwxr-xr-x 7 root root 4096 Jul  9 11:33 /home/
root@SERVER:/home/desktop# ls -ld /home/alfirdaous/
drwxr-xr-x 4 alfirdaous alfirdaous 4096 Sep 20 13:32 /home/alfirdaous/
root@SERVER:/home/desktop# ls -ld /home/alfirdaous/www/
drwxr-xr-x 23 alfirdaous alfirdaous 4096 Oct  1 02:06 /home/alfirdaous/www/
root@SERVER:/home/desktop# ls -l /home/alfirdaous/www/newFile.php 
-rw-rw-r-- 1 alfirdaous alfirdaous 128 Sep 28 04:02 /home/alfirdaous/www/newFile.php

```

---

