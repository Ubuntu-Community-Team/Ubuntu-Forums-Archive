---
title: "permisions issue apache/ubuntu"
date: 2010-07-19
forum: Security
---

### Post by warda on 2010-07-19
hi everyone,
 
I am absolutely new to linux and am trying to learn something new. Have installed apache2 on ubuntu10.
 
created new none sudo user (webadmin) with home folder and directed default website to it
 
/home/webadmin/www
 
then I created website and uploaded it to that folder. thing didnt work and there was error 403. after many heres and theres and applying variety of permisions (please not I never used linux before) I finally run: sudo chmod -R 755 /home/webadmin/*
which seemed to fix problem.
 
then another day i decided change background for websites and uploaded using webadmin user 2 images to folder /home/webadmin/images/
have change html code accordingly (checked many times) image 36.jpg works fine but marb13.jpg not
those are permissions within folder which to me seems even where is the problem?
 
-rwxr-xr-x 1 webadmin webadmin 7718 2010-07-19 17:15 36a.jpg
-rwxr-xr-x 1 webadmin webadmin 4625 2010-07-18 21:11 36.jpg
-rwxr-xr-x 1 webadmin webadmin 177490 2010-07-19 18:34 marb13.jpg
-rwxr-xr-x 1 webadmin webadmin 139057 2010-07-19 18:29 marble13b.jpg
-rwxr-xr-x 1 webadmin webadmin 11612 2010-07-18 21:11 marble13.JPG
 
just to add when I added those 2 images and changed the html code thing didnt work till I rerun sudo chmod -R 755 /home/webadmin/*
 
sorry for this long post just was trying give all possible information.
 
I guess I 'll finish rebuilding entire server... perhaps I did something wrong installing apache on it...
 
thank for enyone taking time in reading

---

### Post by warda on 2010-07-19
bump! 
 
hi again I finally workd it out.:p
 
extention of the file in the html code was JPG instead of jpg - I didnt know capital letters matter for file extentions...
 
anyhow what permission would one recomand for website directory? some people say 755 others say 644. ? 
 
also whenever I add new directory within /www/ I need to rerun permisions, is it normal?
 
dear moderator if you want to remove this treat or move it to diffrent sub forum please do so as it's finally turned out to be spelling/capitalization problem and not a permisions. 
 
thnks everyone

---

### Post by cdenley on 2010-07-19
Everything on Linux filesystems are case-sensitive, not just file extensions. The user apache runs as (www-data) needs access/x permission for the any directory and all parent directories that it needs to read files from. This means 755 for directories. For files, the "x" bit means execution, not access like it does for directories. Files don't need to be executable for apache to serve them. As long as FILES are readable by www-data (644) and ALL parent directories are accessible (755), you should be fine.

This command recursively gives others read permission to everything within a directory, and access permission for directories.
```

sudo chmod -R o+rX /home/webadmin/www

```

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by warda on 2010-07-20
> **cdenley said:**
> 
```

sudo chmod -R o+rX /home/webadmin/www

```
 
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
 
hi thanks,
 
I have applied this permissions. it works fine in browser but now the user webadmin cant change existing files or ad new either using vi or ftp client to load stuff. 
 
I read through the link above and was  runing
 
**sudo chmod 751 /home/webadmin/***
**sudo chmod -R o+rwX /home/webadmin/www**
 
but no luck.
I have to admit am a bit lost with linux permisions :(.
 
I know am asking for shortcut but do you think you could drop a line which would give full permisions for /home/webadmin/www and subfolders to user webadmin?
 
I can add that the owner of the www folder is sudo user admin
 
**drwxr-sr-x 5 admin webadmin 4096 2010-07-19 20:44 www**
 
I tried to run comand to change ownership to webadmin
 
**sudo chown webadmins www**
 
but this didnt seem to do the job.
 
it's all a bit confusing but I guess perhaps my lack of understanding unix/linux principals:oops:
 
thanks

---

### Post by cdenley on 2010-07-20
You can make webadmin the owner
```

sudo chown -R webadmin /home/webadmin/www
sudo chmod -R u+rwX /home/webadmin/www
sudo chmod -R o+rX /home/webadmin/www

```

or assuming the user webadmin belongs to the group webadmin, you can make it the group owner, and give the group owner write permission.
```

sudo chown -R admin:webadmin /home/webadmin/www
sudo chmod -R g+rwX /home/webadmin/www
sudo chmod -R o+rX /home/webadmin/www

```

The safest option is to let only root have write permission, then require root escalation (sudo) whenever changes to web content is needed. You want to minimize the chances that any content you serve can be tampered with, but I'm guessing this isn't going to be a public server, so perhaps this isn't necessary.

---

### Post by warda on 2010-07-20
> **cdenley said:**
>  
The safest option is to let only root have write permission, then require root escalation (sudo) whenever changes to web content is needed. You want to minimize the chances that any content you serve can be tampered with, but I'm guessing this isn't going to be a public server, so perhaps this isn't necessary.
 
 
Hi big thanks for following up. :popcorn:
 
I have built this server for learning purpose so am not much concerned with security however it is accesable from internet (if this is what you mean by public).
 
I'd like to learn good practise though if I one day I was to setup public/ company server on linux/ubuntu platform. 
the purpose of creating webadmin user was let's say you are admin of the web server or group of servers for diffrent companies. now they hire web designer who creates a contecst and use ftp client to upload it to website directory. As I understood to be able to do so he needs to belong to sudo users group?
I didn't make that user part of sudo group intentionally as I didnt want it to have to much powers on the server... just enough to save/modify contecst of certain web directory
is it possible that you have nosudo enabled user who can using ftp client login into server and change anything he/ she wants within only that certain web directory?
 
t..

---

### Post by cdenley on 2010-07-20
> **warda said:**
> is it possible that you have nosudo enabled user who can using ftp client login into server and change anything he/ she wants within only that certain web directory?


Yes, this is possible. You can grant write permission to whoever you want, and most FTP servers have a chroot option. Obviously permitting any remote write access to the files opens up more possibilities for these files being modified maliciously, but this is sometimes necessary. Using plain FTP without requiring encryption would make this much more likely, though.

---

### Post by warda on 2010-07-20
> **cdenley said:**
> You can make webadmin the owner
 
```

sudo chown -R admin:webadmin /home/webadmin/www
sudo chmod -R g+rwX /home/webadmin/www
sudo chmod -R o+rX /home/webadmin/www

```
 

 
sorry actually above code supplied by you earlier answers the question.
so webadmin is not sudo user but with above applied permissions is able to modify contecst.
 
thanks

---

### Post by warda on 2010-07-20
looks our replays overlapped :)
 
 thanks for explaining things I think slowly am getting to the right place with linux permissions ;)
 
cheers

---

