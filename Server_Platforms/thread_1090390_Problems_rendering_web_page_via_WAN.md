---
title: "Problems rendering web page via WAN"
date: 2009-03-08
forum: Server Platforms
---

### Post by cje on 2009-03-08
I have a strange problem with one of my webfolder on my webserver. 

In /var/www I have several folders. 
One of the folders has been named "testserver" and have some subfolders with projects I would like to test and tweak before going online.

These webpages are working normal on my LAN network. But, when accessing the pages from WAN it's rendered very slow and w/o pictures. Some of the test projects doesn't show up at all via WAN (due to too long respond time).

The problem is not related to the type of webpage it self as I have similar pages under other folder and I have similar problems with different type of pages. 

Thanks for any suggestions.

---

### Post by cje on 2009-03-10
anyone?

---

### Post by cje on 2009-03-11
I think I'm into something. Yesterday, I got the same problem in another web folder when I added a password to htaccess (using htpasswd). 

On the other side, I do also have password protected other folders w/o this problem. But, as far as I remember, these folders doesn't use MYSQL... 

So, now I need to know how to password protect a web folder w/o having the rendering problem....

---

### Post by cje on 2009-03-11
This is part of my apache2.conf

> <Directory /var/www2/site2>
AllowOverride All
</Directory>


And this the .htaccess file for site2

> AuthUserFile /var/www2/site2/.htpasswd
AuthName "Authorization Required"
AuthType Basic
require valid-user

# BEGIN WordPress

# END WordPress

---

### Post by cje on 2009-03-12
I've decided to close this thread and start a new one with a more exact title.

---

