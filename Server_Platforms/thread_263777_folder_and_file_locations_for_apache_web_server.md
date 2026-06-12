---
title: "folder and file locations for apache web server"
date: 2006-09-23
forum: Server Platforms
---

### Post by Geoff2077 on 2006-09-23
Is there a recommended folder structure to use when setting up a web server. I would like to know where the different files should be stored, that go to make up the content of the web pages.
Geoff

---

### Post by bluefrog on 2006-09-27
if you are to put your websites in /var/www then eventually you could have /var (or /var/www) on a separate partition.

Then of course it all depends on where you want to keep your website files and folders.

James

---

### Post by Geoff2077 on 2006-09-27
James,
is it then usual to have spearate folders under /www/ for say /graphics; /cgi_bin; 
I was wondering what is considered to be best practice.

Thanks
Geoff

---

### Post by bluefrog on 2006-09-27
I will not be able to answer you straight on that one.
I use apache but I am far from understanding everything. 

regarding cgi_bin that would be a security problem (I think) to have them in /var/www (that's why they are somewhere else). To find  out where they are have a look at /etc/apache2/apache2.conf.

creating folders and subfolders depends on how you like to order your work...

you are not obliged to put a website in /var/www. you can put it anywhere you like and do correct aliasing (for example) in the apache2.conf (or maybe in /etc/apache2/sites-avalaible...

You should read [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) and other docs to get a grip on apache

james

---

### Post by ejpyle on 2008-04-30
I am lost....installed Apache and the test page came up....went into "sites-enabled" and changed the conf file to show doc root as /www/public_html/

i stop and start apache and it still reverts to the old /var/www/

what gives?

---

