---
title: "Webserver permission"
date: 2015-03-24
forum: Server Platforms
---

### Post by snipershady-n on 2015-03-24
I've a permission problem on my dedicated webserver, but I'm not able to understand what's I was doing wrong.

Ubuntu 14.04
Kernel 3.19.2
Versione Apache 2.4.7
Versione PHP 5.5.9
mysql 5.5

(all from official repository, except for kernel. It comes from vivid repository)

I've installed apache2 and it starts with user
www-data

I've set a virtualhost
/home/USER1/public_html
(where chown is USER1:USER1)

so If I install any CMS (like joomla, wordpress or phpbb)
I got lot of permission's problem and I'm forced to set chmod to 777 (OMG! Against common sense)
in order to install one of them.

The "standard" chmod for this kind of CMS is
755 for directory
644 for files

but if I set this kind of permission, I cannot do anything with the cms (install anythink or update it. Files will be considered unwritable).
Same problem with 775 
So the problem is that my webserver needs all permission to "OTHER" and not just for USER (or at least fro GROUP)

In order to avoid this trouble I've added USER1 to www-data group 

```
usermod -a -G www-data USER1

```

but files still unwritable with 775 or 755. The only chmod allowed still 777 (OMG is orrible to write it 2 times in the same post :D )


What is the problem?
What I'd have to do in order to fix that trouble?


Thank you for support

---

### Post by nerdtron on 2015-03-24
First, even if you add www-data to the group USER1, www-data won't be able to write on folders owned by USER1.
Why? because of 755, which means, the owner has full permissions, while members of the group and other users will only have read permission. Same principle for 644 permissions.

You might wanna try 775 for folder and 664 for files and you should be able to write on USER1 and www-data.
Permissions are a bit hard to understand but once you get the knack of it, it all comes down to you.
Some readings: [http://ryanstutorials.net/linuxtutorial/permissions.php](http://ryanstutorials.net/linuxtutorial/permissions.php) and [https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions](https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions)


Next, I don't think you will be able to use the folder /home/USER1 folder to hold your webpages. Apparmor will prevent you from using non-default directories. You may want to try those permissions on /var/www/html directory.

---

### Post by snipershady-n on 2015-03-24
As you can read I've wrote
"same problem with 775"

I know how it works
u    g     o
rwx rwx rwx 
111 111 101

I know how to convert binary to octal

Are you sure that the beste way is to use the /var/www/ for every virtualhost too ??
And how the "user1" will be able to handle any permission on /var/www ? A directory with CHOWN root:root !!!!!

```

ls -al |grep www
drwxr-xr-x  3 root root   4096 Mar 17 20:15 www


```

---

### Post by nerdtron on 2015-03-24
ok, post your folder that you said won't work with 775, 
```
 ls -la /home/USER1
id USER1
id www-data

```

And the default folder location for webpages is the /var/www/html even for virtualhosts too. And permissions on ownership on that folder won't matter (although it should be owned by www-data). As long as the file inside /var/www/html/ is world readable, then apache will display it.

---

### Post by snipershady-n on 2015-03-24
right now is set as the awful 777 (and it works)

```

ls -al /home/USER1
total 32
drwxr-xr-x  4 USER1 USER1 4096 Mar 18 15:50 .
drwxr-xr-x 21 root             root             4096 Mar 17 19:48 ..
-rw-------  1 USER1 USER1 2231 Mar 23 23:15 .bash_history
-rw-r--r--  1 USER1 USER1  220 Mar 17 19:48 .bash_logout
-rw-r--r--  1 USER1 USER1 3637 Mar 17 19:48 .bashrc
drwx------  3 USER1 USER1 4096 Mar 18 15:50 .config
-rw-r--r--  1 USER1 USER1  675 Mar 17 19:48 .profile
drwxrwxrwx  4 USER1 USER1 4096 Mar 18 20:17 public_html


``` 

```

 cat /etc/passwd | grep www


www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin

id www-data
uid=33(www-data) gid=33(www-data) groups=33(www-data)




```


```

cat /etc/passwd | grep USER1
USER1:x:1018:1018:,,,:/home/USER1:/bin/bash

id USER1
uid=1018(USER1) gid=1018(USER1) groups=1018(USER1),33(www-data)




```

I wrote a script to quicly reset all permission

```
#!/bin/bash
directory=777
files=777
find /home/USER1/public_html/ -type d -print0 | xargs -0 chmod $dire$
find /home/USER1/public_html/ -type f -print0 | xargs -0 chmod $file$

chown -R USER1:USER1 /home/USER1/public_html


```

anything else?

---

### Post by nerdtron on 2015-03-24
Seems correct. Now who is the user that needs to "write" on the /home/USER1 folder? Right now, only USER1 will be able to write that folder.

If you need www-data to write on that folder, your need to add other users on the USER1 group, but what you did is the opposite, adding USER1 to www-data group, which won't help here.

---

### Post by snipershady-n on 2015-03-24
With 777 it works fine. But is awful

I'd like to set it 755 for directory and 644 for files (and 444 for config.php files of the cms)

so you'd think I'll fix with a simbple

```

usermod -a -G USER1 www-data 
```

---

### Post by snipershady-n on 2015-03-24
DONE! 
usermod -a -G USER1 www-data
chmod set to 755 to file and folders (just to test it quickly)

**It still doesn't works!**
All directory and files are "unwritable" for the CMS 
GRRRRRRRRRRRRR!!!!

---

### Post by nerdtron on 2015-03-24
755 won't work, the minimum is 775 since you are writing as a member of a group not as the owner.

what user is used by CMS to write files?

---

### Post by snipershady-n on 2015-03-24
really a good question!

I do not know! If I upload a file via ftp as user1, I can write anything.
But I really do not know what the cms want 

Anyway RIGHT NOW
i changed my "permission.sh" script 

I've set
usermod -a -G USER1 www-data 

as suggested by you, but I've set too
chown -r user1:www-data /home/user1/public_html

NOW it works with 775 (better then the awful 777. Just User and Group are able to works on that files and directories)


I'd like to understand how is configured the webserver of every common hoster, where I'm able to set 755 and 644 for files without problems!

P.s. thank you for your support. I do really appreciate it

---

### Post by snipershady-n on 2015-03-24
Do you think I can fix installing ??

mpm worker
mod fcgid
suexec custom
php cgi

what do you think about that?

---

### Post by snipershady-n on 2015-03-24
that was the way (one way, maybe not the best one, but a good solution)

-add www-data to user1's group
-chown user1:www-data public_html

```
chmod g+s /home/user1/public
```

---

### Post by nerdtron on 2015-03-25
> Do you think I can fix installing ??

mpm worker
mod fcgid
suexec custom
php cgi

what do you think about that?

As your problems are on permissions, I don't think installing additional packages will solve the problem.

> -add www-data to user1's group
-chown user1:www-data public_html
Yep, its one way of doing things and it's more secure than 777. I don't have further suggestions as I don't use 775 on web services folders.

---

