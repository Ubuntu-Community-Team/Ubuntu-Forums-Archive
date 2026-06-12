---
title: "Need Help With Nginx and WordPress"
date: 2015-04-28
forum: Server Platforms
---

### Post by danny46 on 2015-04-28
Hi,

I am new in Linux so please go easy :D

I followed a tutorial on a certain webhost company (DO), about setting LEMP stack, WordPress and PHPMyadmin. My goal is to eventually host several websites on 1 VM (may or may not related).

During the tutorial, I created the database and installation folder with a "common" name (eg: wordpress, html etc), and it worked. But then I decided to change the installation folder and database to more "synchronize" - name wise - with my sites, so, lets say that I changed the root folders into "site1", "site2" and "site3", and same goes for the database name ("wordpress" changed to "site1").

It worked when I (only) changed the folder name, but it then I changed the data base then it broke. 
Needless to say, I have edited the nginx config and wp-config.php (db-name) to reflect the changes. 
I also restart nginx and php5-fpm, changed the links / directories path needed. 
I put a php info test file inside the WP folder and it is accessible (site-name.com/info.php), also PHPmyadmin works (site-name.com/phpmyadmin). 
Nginx -t completed without error.

The error is: right now if I type the site address it only display a blank screen. 

My questions are:
1. What else could I miss ..?
2. How do I debug this / can search where the error is? Again, I am new in Linux, so.. please explain like I am five lol

Thanks in advance!

---

### Post by danny46 on 2015-04-29
Solved. I forgot to create a new user and adding it to the new database :P

---

