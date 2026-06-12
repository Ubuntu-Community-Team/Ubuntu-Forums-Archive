---
title: "PHP Configuration Problems?"
date: 2009-11-24
forum: Server Platforms
---

### Post by sitservices on 2009-11-24
I have tried moving Wordpress, BBPress and KB-Publisher from shared hosting to a dedicated Ubuntu server running Ubuntu Server 9.10
 
For those of you familiar with the packages I took a .SQL dump from PHPMYADMIN on the shared hosting, created a new database in MySQL 5 (installed via apt-get) and imported the database (having already changed any references to the old domain to the new domain using find/replace in Notepad++). I then created the same MySQL username and password in the local console (the server is remote and as such I've only installed Command Line) and granted ALL permissions on the database (* tables).
 
WP-Config.php has been amended with the new domain name and to give localhost as the MySQL server address.
 
This is all as per the instructions for changing servers/domains with WPMU and I can't find any steps I've missed out. 
 
I can see individual blogs and posts and some of the config pages but mostly when I visit pages, especially indexes, I see a directory listing (see below). On some pages I see a blank page.
 
[IMG]http://www.sallyandpeter.co.uk/screenshot.JPG[/IMG]
 
As KB Publisher is doing the same and is unrelated apart from being a PHP/MySQL package is there any server config I have overlooked in my ignorance.
 
There is no .htaccess common to the three folders (all are directly below /var/www/ e.g. /var/www/blogs/) and mod-rewrite has been enabled.
 
Permissions look the same as on the previous server.
 
Thanks in advance for any help.

---

### Post by i.r.id10t on 2009-11-24
You need to add index.php to the directoryindex list-o-files

---

### Post by sitservices on 2009-11-24
If I visit index.php in the address window it just directs me back to /blogs/ - I will try this though.

---

