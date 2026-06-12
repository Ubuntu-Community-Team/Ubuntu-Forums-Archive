---
title: "Permissions help"
date: 2008-08-07
forum: Server Platforms
---

### Post by heyman12 on 2008-08-07
Ok, I just installed proftpd, webmin, and ubuntu LAMP, I created a new user with webmin, and then set the home directory as /var/www. I logged in, just fine, but I can only copy and read, not write. 
I've tried to use root, but root cant log in, and my sudo user wont work either. How can I set the permissions to X user can write to FTP as well as read and copy?

---

### Post by StickyStyle on 2008-08-07
If you look at /var/www you will see it is owned by root:root with the perms set at 755, that is why you cannot write.  Any reason you set the home directory to that?

---

### Post by heyman12 on 2008-08-07
It is an FTP user, and that is where the http docs are, so I can go and change them. Is there a command I can use to go edit the permissions or something in webmin I can set the ownership to this user?


I am a complete beginner at Linux...

---

### Post by StickyStyle on 2008-08-07
Sorry, I don't really know anything about webmin (although I do see people recommending the use of ebox over webmin).

If you really wanted to you could change the owner of /var/www to the user you want, but I wouldn't recommend that route. I would also not set a users home directory in any directory under /var/www, as then you are exposing a users home directory to the world. In the course of using a linux system the OS will create lots of hidden folders like ~/.ssh and that folder is  now accessible to the world.  Apache includes in it's configuration by default disallowing reading of hidden files, but not hidden directories.

Not really knowing exactly what your trying to accomplish with the site, you could create a directory /var/www/somesite and set your user as the owner of that directory so they can put files there.  But they have a normal home directory like in /home/someuser

---

### Post by heyman12 on 2008-08-07
Well the reason why I'm having the home directory as the www folder is because I'm getting a linux LAN only web server up, and I need to access and be able to write to these files.

---

### Post by windependence on 2008-08-08
You don't need to have the document root as your hoome directory to do this, you just need to set ownership of that directory correctly so that you will be permitted to write to the directory. As sticky suggested, create a subdirectory and change the ownership to your user. Then, the user can access the files without having the directory as their home.

-Tim

---

### Post by cariboo on 2008-08-08
My preferred way of doing what you want without screwing up ownership and permissions, is to make sure everything in /var/www is owned by www-data.www-data
 and has file permissions of 755. Then create a symlink to the users directory for example in /var/www:

```
ln -s /home/<user>/html html
```

Where <user> is the your username, then change the doc root to point to /var/www/html. That way you can add, remove or change the files in your home directory and have them show up when you access them from the internet.

Jim

---

### Post by Kolipoki on 2008-08-08
> **cariboo907 said:**
> My preferred way of doing what you want without screwing up ownership and permissions, is to make sure everything in /var/www is owned by www-data.www-data
 and has file permissions of 755. Then create a symlink to the users directory for example in /var/www:

```
ln -s /home/<user>/html html
```

Where <user> is the your username, then change the doc root to point to /var/www/html. That way you can add, remove or change the files in your home directory and have them show up when you access them from the internet.

Jim
Well this issue of chowning /var/www to www-data:www-data keeps coming back to me (another noob). I recently started a thread with that topic here: [http://ubuntuforums.org/showthread.php?p=5527748#post5527748](http://ubuntuforums.org/showthread.php?p=5527748#post5527748) , precisely after reading this aparently contradictory info (at least to our noob eyes). 

Please someone elaborate a bit. Seems there can be different situations where you can use one or another option. Mighty thanks in advance for the time and patience. K.

---

### Post by StickyStyle on 2008-08-08
Well, cariboo907 said everything *under* /var/www, not /var/www which I am against. I still stand by my statement though in the referenced post that giving www-data carte blanche access to everything under /var/www/ is a bad idea also though for the reason that an exploited web application could then overwrite files, potentially then serving up malware.

However his idea of doing a symlink is a valid one, you just have to make sure the FollowSymLinks is turned on for the <Directory> for apache to use it.
[http://httpd.apache.org/docs/2.2/mod/core.html#options](http://httpd.apache.org/docs/2.2/mod/core.html#options)

---

### Post by Kolipoki on 2008-08-08
Kk, maybe this was a bit of a "Lost in translation" affair :) Cariboo posted "..in /var/www", which made me think that *www* was included as well. Thanks again Sticky...:guitar:

EDIT: BTW, do you need to assign a password to www-data?

---

