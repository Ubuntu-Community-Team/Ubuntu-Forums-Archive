---
title: "PHP Accessing files that are back a directory"
date: 2007-05-14
forum: Server Platforms
---

### Post by JonasE on 2007-05-14
I am making a simple thing with php and my problem is that I have files that are back from the web root /var/secure instead of /var/www and I want to be able to access those files in the secure folder from my php pages in the www folder. I dont know if im missing something real simple but I did try using the ".." in my file path to go back a dir, but wasnt able to get it to work.

Over and out,
  Jonas E.

---

### Post by Wim Sturkenboom on 2007-05-14
Check the permissions on the directories. You can temporarily give full permissions on the directories and check if it solves the problem. If so, you can finetune the permissions.

What errors does PHP give ?

---

### Post by JonasE on 2007-05-14
Well I am just using a if (file_exists) deal to make sure the file exists first but it doesnt find it so I get the error: cannot stream file or whatever.

Are you saying your able to change the permission of certain folders in php?

Are you able to move back a directory in php to find files?

Thanks,
  Jonas E.

---

### Post by Wim Sturkenboom on 2007-05-15
No, change permissions at system level.

And yes, you can move back.

```

wim@btd-techweb01:~$ ls -ld tacinc
drwxr-xr-x  4 wim develop 96 2007-03-27 06:41 tacinc/
wim@btd-techweb01:~$ ls -l tacinc
total 2
drwxr-xr-x  7 wim develop  264 2007-02-08 06:43 inc/
drwxr-xr-x  4 wim develop 1280 2007-03-26 13:20 web/
wim@btd-techweb01:~$

```
*tacinc* is a website; visitor accessible files (i.e. index.php) are in *web* so it's the document root. Include files for php are in *inc*. Apache runs on my (Slackware) system as user nobody; for apache to be able to read files in inc, the permissions for *other users* need to be set to 5 (read and execute).

---

### Post by primski on 2007-05-15
you can just use absolute path like include("var/secure/file.php");

---

