---
title: "How to add Perl to apache2"
date: 2007-07-08
forum: Server Platforms
---

### Post by twistedtwig on 2007-07-08
Hi all,

I have been fighting with this for a while.  I tried to install AWSTATS and found that I didn't have perl installed. 

I downloaded (what i think was) all the perl modules needed.  
I have the awstats.pl in /usr/lib/cgi-bin.  
I have a symbolic link from /var/www/root/cg-bin that points to /usr/lib/cgi-bin (www/root is my root folder for net access rather than just www/ )

When i put houseofhawkins.com/cgi-bin/awstats.pl into the browser I can asked if I want to download the file rather than it being run.

I am going round in circles now and don't know where to go to get this fixed.

I hope you maybe able to help.

Thank you

---

### Post by waster on 2007-07-08
Default permissions is probably not to run cgi unless explicitly allowed. This could be a .htsomething file or in the apache config. I presume you have libapache2-modperl installed...

---

### Post by waster on 2007-07-08
oh, and check ownership of the symlink and the cgi script.

---

### Post by twistedtwig on 2007-07-08
I have uncommented "AddHandler cgi-script .cgi" within /etc/apach2/apache.conf

usr/lib/cgi-bin has the following permissins:

drwxr-xr-x  2 root root     4096 2007-07-08 09:50 cgi-bin

/var/www/root has the following permissions

lrwxrwxrwx 1 root   root      17 2007-07-08 09:56 cgi-bin -> /usr/lib/cgi-bin/
-rwxr--r-- 1 nobody nogroup 7214 2007-06-28 20:16 externallinks.html
-rwxr--r-- 1 nobody nogroup 3751 2007-06-27 22:39 faq.html
-rwxr--r-- 1 nobody nogroup  959 2007-06-25 22:15 feed.xml
-rwxr--r-- 1 nobody nogroup 5685 2007-06-27 22:47 games.html
-rwxr--r-- 1 nobody nogroup 8668 2007-06-27 22:40 hardware.html
drwxr-xr-x 2 nobody nogroup 4096 2007-06-23 10:16 images
-rwxr--r-- 1 nobody nogroup 9746 2007-07-04 19:35 index.html
drwxr-xr-x 9 nobody nogroup 4096 2007-06-28 20:05 old
drwxr-xr-x 6 nobody nogroup 4096 2007-07-04 20:08 projects
-rwxr--r-- 1 nobody nogroup   23 2007-06-21 22:18 robots.txt
-rwxr--r-- 1 nobody nogroup  234 2007-06-21 22:18 rounded.css
-rwxr--r-- 1 nobody nogroup 4189 2007-06-26 22:49 rounded.js
-rwxr--r-- 1 nobody nogroup 5115 2007-06-27 22:40 rss.html
-rwxr--r-- 1 nobody nogroup    0 2007-06-24 09:54 sitemaphtml.php
-rwxr--r-- 1 nobody nogroup  101 2007-06-23 19:49 sitemaplinkinfo.php
-rwxr--r-- 1 nobody nogroup  683 2007-06-23 19:57 sitemapraw.php
-rwxr--r-- 1 nobody nogroup    0 2007-06-24 09:53 sitemapxml.php
-rwxr--r-- 1 nobody nogroup 3623 2007-07-05 17:44 style.css
-rwxr--r-- 1 nobody nogroup 3541 2007-07-04 19:38 template.html

I am not honestly sure what permissions things should have and am nervous of giving away too many permissions when I don't understand its implications.

Thank you for any and all help

---

### Post by twistedtwig on 2007-07-09
I am still not sure about the permisssions.

But during my investigations I found something (didn't fix my issue but might help jog someone elses mind I hope):

within apache2.conf

I have uncommented:

AddHandler cgi-scrpt .cgi

But i was told to add .pl:

AddHandler cgi-scrpt .cgi **.pl**

also to do:

<Directory />
Options followsymLinks
AllowOverride None
</Directory>
 
change to:
 
Options followSymLibks +ExecCGI

the only place I could find this was in /etc/apach2/conf/vhosts/vhosts.conf in the root file path.

but when I restarted apache it still did the same do you want to download this file bit :(

---

### Post by twistedtwig on 2007-07-09
It works :D

I have to change the permissions to chmod a+x

then the test.pl worked

---

