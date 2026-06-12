---
title: "Apache2, MySQL, VHOSTS"
date: 2010-10-23
forum: Server Platforms
---

### Post by piine on 2010-10-23
Hi, I was just wondering, is there a way to use mysql to create vhosts for apache2 and if there is a way to startup new vhosts without having to reload apache2 or a secure method of restarting apache2 with user www-data... 

FYI: I am building a small scale web admin cp... nothing big, I just want to be able to have everything automated... got dns, ftp and mail able to add users on the fly, now if I can just get apache2 to do the same, I will have reached success, so pls, community, HELP!!!

Also, if anyone has info on exactly how to quota apache2 users and bandwidth with a mysql DB, that will be great as well... emphasis on bandwidth quota

---

### Post by Ryan Dwyer on 2010-10-23
Have a look at my recent post here about giving www-data permission to do stuff:
[http://ubuntuforums.org/showthread.php?t=1603477](http://ubuntuforums.org/showthread.php?t=1603477)

You'd want to add a2ensite and a2dissite to the command list so it can enable and disable vhosts. Also change the permissions in /etc/apache2/sites-available/ so www-data can write to it.

I don't think Apache has any functionality to read vhosts from a MySQL database, but this works just as well.

---

