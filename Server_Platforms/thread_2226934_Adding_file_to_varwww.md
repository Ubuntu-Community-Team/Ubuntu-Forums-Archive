---
title: "Adding file to /var/www/"
date: 2014-05-29
forum: Server Platforms
---

### Post by Jordan_Hickin on 2014-05-29
Hi everyone

I have a file saved under /home/jordan/Desktop/PHPWEB/PHPWEBSITE/index.php

I am trying to put it in /var/www/index.php

It never lets me. always saying the /var/www/index.php not found... or /var/www/ is not a directory

I have tried saving it to my /home/adminjah/ folder on the server... it has files in it already which i can view using ls /home/adminjah. but it too says /home/adminjah/ no such directoy.

Please help me

---

### Post by TheFu on 2014-05-29
It is time to learn about directories, files and UNIX/Linux permissions.
google "ubuntu permissions" and follow the tutorial to get a beginning level understanding.

In the meantime, run these commands:
```

sudo mkdir -p /var/www/
sudo mv /home/jordan/Desktop/PHPWEB/PHPWEBSITE/index.php /var/www/index.php

```
Then you'll want/need to change the owner, group and possibly the permission bits as needed.

---

### Post by Jordan_Hickin on 2014-05-29
sorry either i misunderstood or maybe i didnt make it clear


I am able to mv items between the folders on the server without problem.. i have removed the old webpage from /var/www/.... the problem i am having is placing the file on the server from my desktop via the terminal/ i have ftp.

the permissions having been adjusted since i last use it when it worked.. but it was long ago and i can't remember how i got the files on there.

---

### Post by TheFu on 2014-05-29
Please be explicit.
1. What is the server account userid?
2. What are the files in /var/www - please use **ls -al /var/www** so we can see the ownership, groups and permission bits. Hopefully, you will login using ssh.

FTP is bad and [shouldn't be used anymore]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp") (for the last 15 yrs). If that is all the hosting provider provides, it is time to find a new webhost.

---

### Post by kosmokramer314 on 2014-05-29
log into the server via ssh and
```
cd /var
ls -ltrh
```

what is the output?

---

### Post by Jordan_Hickin on 2014-05-29
Okay... more information.

The server in a local only server which i built out of an old tower. (it was well past its use by date, perfect for a first time server)

kosmokramer314: here is the part you asked for
```

adminjah@webserver1:~$ cd /var
adminjah@webserver1:/var$ ls -ltrh
total 44K
drwxrwsr-x  2 root staff  4.0K Apr 10 23:12 local
drwxr-xr-x  2 root root   4.0K Apr 10 23:12 backups
drwxr-xr-x  2 root root   4.0K Apr 16 22:02 opt
drwxrwsr-x  2 root mail   4.0K Apr 16 22:02 mail
lrwxrwxrwx  1 root root      9 Apr 28 18:45 lock -> /run/lock
drwxr-xr-x  5 root root   4.0K Apr 28 18:45 spool
lrwxrwxrwx  1 root root      4 Apr 28 18:45 run -> /run
drwxrwxrwt  2 root root   4.0K Apr 28 18:54 crash
drwxr-xr-x 41 root root   4.0K Apr 28 19:16 lib
drwxr-xr-x  9 root root   4.0K Apr 28 19:16 cache
drwxrwxrwt  2 root root   4.0K May 29 18:35 tmp
drwxr-xr-x  4 root root   4.0K May 29 21:17 www
drwxrwxr-x 12 root syslog 4.0K May 29 22:06 log

```
 TheFu: here is yours:
```

adminjah@webserver1:/var$ ls -al /var/www
total 16
drwxr-xr-x  4 root     root 4096 May 29 21:17 .
drwxr-xr-x 13 root     root 4096 Apr 28 19:16 ..
drwxr-xr-x  3 root     root 4096 May 29 21:51 html
drwxr-xr-x  3 webuser1 root 4096 Apr 28 21:47 webuser1

```


I have ssh. and ftp was a quick fix to a problem i had ages ago. i am up for using any method atm as it is only local.

at the moment /var/www/ only contains another folder /webuser1/ which contains a /index.html

server account user ID is adminjah


all i want to do is to add a php website i have built.

the php website is in my documents on ubuntu desktop under  PHPWEBSITE

i can add the files to here if it helps

hope this helps

---

### Post by TheFu on 2014-05-29
Use sftp, filezilla, or winscp - all should be configured for the sftp protocol. This is secure, unlike FTP.

The userid you need access is webuser1 and/or root.  adminjah doesn't appear to be useful at all, unless it has sudo permissions.
Did you go through that file/directory permissions tutor yet? [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Jordan_Hickin on 2014-05-29
adminjah is the sudo account on the server.. webuser1 was added by adminjah. i will be moving the webuser 1 folder as it is not needed anymore.

adminjah has access to root permissions. and i am going through it

---

### Post by TheFu on 2014-05-29
> 
sudo mkdir -p /var/www/
sudo mv /home/jordan/Desktop/PHPWEB/PHPWEBSITE/index.php /var/www/index.php

What is wrong with these commands?  Is it just that you need to push the file?  If so:```

scp /home/jordan/Desktop/PHPWEB/PHPWEBSITE/index.php webserver1:
ssh webserver1
sudo mv index.php /var/www/index.php
```

---

### Post by Jordan_Hickin on 2014-05-29
it just says: /home/jordan/Documents/PHPWEBSITE/index.php: No such file or directory

i moved the folder to that location.. so desktop wasn't causing any problems

---

### Post by Jordan_Hickin on 2014-05-29
Done it

I ran

scp /home/jordan/Documents/PHPWEBSITE/index.php adminjah@192.168.0.7:/home/adminjah

That put it on the server

then i i did sudo mv /home/adminjah/index.php /var/www

and it is now in the folder.

thanks :D

---

