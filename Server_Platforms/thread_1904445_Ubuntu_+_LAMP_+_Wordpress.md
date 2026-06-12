---
title: "Ubuntu + LAMP + Wordpress"
date: 2012-01-04
forum: Server Platforms
---

### Post by Boffen on 2012-01-04
Hi,
I have installed the latest version of Ubuntu server, LAMP and wordpress.
Everything with standard settings and it seems to be OK until i Publish a new page. It looks OK in wordpress but when i'm going to view the new page I get the error message:
 
"The webpage cannot be found"
 
Anyone know how to solve this? Probably a security setting somewhere but I have no idéa where...
 
Thanks for advice

---

### Post by dazman19 on 2012-01-05
it sounds like a wordpress specific issue.

When you install wordpress it wont actually set itself up properly unless you have php/mysql/apache2 installed properly. So If you installed wordpress and can access the control panel for it then it could be the way the URL's are being written.

if you installed wordpress and moved the wordpress folder to another subfolder later on then the could cause that problem. If this is the case then i suggest you either add a symbolic link to where it was OR find out where in the wordpress config you can change it.

I would be looking at wordpress support places. Perhaps it could be an issue with mod-rewrite, but unless you have installed some fancy wordpress plugin or something it is probably not the case.. to rule it out try

sudo a2enmod rewrite

If it says it is already enabled then i suggest you see if you can find someone to help you with the wordpress framework. They will probably want you to paste configuration files etc. 

if you can run a phpinfo 

e.g. make a file called 
phpinfo.php and put this in it:
[PHP]
<?php phpinfo(); ?>[/PHP]
then browse to it, and it says mysql etc is all enabled then it must be a problem with wordpress.

---

### Post by Boffen on 2012-01-05
Thanks dazman19,
I did what you suggested to ask wordpress, and yes the problem was the "permalinks" settings. I needed to edit the .htaccess file.
 
Here is more info if someone else have the same problem.
[http://codex.wordpress.org/Using_Permalinks](http://codex.wordpress.org/Using_Permalinks)

---

