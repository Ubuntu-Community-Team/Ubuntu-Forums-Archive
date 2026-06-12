---
title: "apache and /var/www and PHP"
date: 2007-01-04
forum: Server Platforms
---

### Post by kramerkeller on 2007-01-04
This is very odd.  I created a hello world file under /var/www.  I wrote this file in php.  I accessed my server and it all worked fine.  

I can write new files in vi that are php save them in www and view them fine.  I can create directories and view them.  

However, I tried to take some existing php files that ran on another machine.  I can move files into /var/www, but for some reason files moved or copied show up in the terminal, but not on the server.

This is a problem.  I wrote php files on my mac and tried after putting them onto my linux server in /var/www it shows up in the terminal, but not online.

I did notice one odd thing.  In the terminal the files that I transferred that are .php are green and the files I wrote are black.  Both seem to be fine and complete in vi.

Please Help

---

### Post by kebes on 2007-01-04
The most likely explanation is that the files you've copied into /var/www/ have restricted permissions. For the webserver to access them (and send them on to whoever requested them), the permissions must be right. To do that right-click on them in your file browser and change the permissions, or on the commandline use the command "chmod" to modify.

---

### Post by kramerkeller on 2007-01-04
I think I see.  Alright, how would I go about using chmod to change the permissions so that the files can be viewed by all on the apache server.

When I try to view a page I pulled from the directory and chmod 700ed I get this

Warning: Unknown(/var/www/Index.php): failed to open stream: Permission denied in Unknown on line 0

Warning: (null)(): Failed opening '/var/www/Index.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

---

### Post by kebes on 2007-01-04
Go to the directory in question:
$ cd /var/www/

Then use chmod to change the permission:
$ sudo chmod +r index.php
or
$ sudo chmod 644 index.php


After doing this check the permissions:
$ ls -laF

You will see something like:
```

kebes@computer:/var/www$ ls -laF
total 40
drwxr-xr-x  8 root  root  4096 2006-10-10 19:41 ./
drwxr-xr-x 14 root  root  4096 2006-09-20 21:12 ../
drwxr-xr-x  2 root  root  4096 2006-09-20 21:12 apache2-default/
-rw-r--r--  1 kebes kebes 787 2006-10-01 13:37 index.php

```

Notice that "index.php" has a "r" (i.e. "read permission") for all three security levels (the user who owns the file, the group that owns the file, and "the world"). Notice also that only the fileowner ("kebes" in the output above) has "w" (i.e. "write permission") so other people can't delete the file.

---

### Post by kramerkeller on 2007-01-05
Thank you so much - do you know how I can do this with an entire file - would I do recursive or something

I added a whole file of those php files and would like not to have to chmod all of them

---

### Post by kebes on 2007-01-05
Yes doing a chmod recursively is easy. Let's say you put the directory "newsite" into "/var/www/" and want to change it (and all the contents), you just go:

```

cd /var/www/
chmod 644 newsite/ -R

```

The "-R" switch makes it recursive. (With any unix command, you can type "man command" to get more information about it. So "man chmod" will bring up the _man_ual page for chmod.)

Hope that helps.

---

### Post by kramerkeller on 2007-01-08
Thank you so much this problem is solved

---

