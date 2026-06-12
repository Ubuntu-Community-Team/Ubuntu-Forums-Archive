---
title: "Apache and PHP --Confused I am."
date: 2007-04-04
forum: Server Platforms
---

### Post by Rush_898 on 2007-04-04
I am attempting to install Cacti for monitoring purposes.  I have followed this FAQ:

[http://www.ubuntugeek.com/networkserver-statistics-graphing-using-cacti-in-ubuntu-server.html#more-85](http://www.ubuntugeek.com/networkserver-statistics-graphing-using-cacti-in-ubuntu-server.html#more-85)


Everything was going along fine until the moment of truth when I tried to actually go the IP of the server (this is an internal server no FQDN).  I have MRTG on the same server and it was running fine so I can pull up the IP of the server and view the mrtg stuff.  There was a cacti folder as indicated in /var/www/cacti but when I tried to access it there was nothing.  No messages, no pages, no nothing.  I finally figured out that Apache was having problems w/ PHP since all problematic pages were php.  I did some surfing around and found this page:

[http://www.debianadmin.com/apache2-web-server-with-php-support-in-ubuntu.html](http://www.debianadmin.com/apache2-web-server-with-php-support-in-ubuntu.html)

Thinking it hadn't taken before I ran this command:

> sudo apt-get install libapache2-mod-php4 php4-cli php4-common php4-cgi

That ran telling me it was replacing php5, so I thought fine at least I know it has 4 now for sure.

I noticed they showed it necessary to restart the apache process.  So I did that.  Then it has a way to test php functionality:

> Test apache with PHP
To test if php4 installed correctly

sudo gedit /var/www/test.php

Insert the following line into the new file

<?php phpinfo();?>

Save this file

Now access this page [http://yourserverip/test.php](http://yourserverip/test.php) you should see the following screen


I did this and I get the same thing that I get when I try to access any php now.  The browser will try to download the index.php or whatever page thinking it is a file and not parsing it as an actual web page.  I have tried everything I can think of and am now confused.

Please if you have advice, or a webpage to reference.  I think I have cacti up and going.  It is apache possibly at this point that is giving me grief with php content.

Thanks!

---

### Post by joebeasley on 2007-04-04
**Add index.php to your httpd.conf.**
DirectoryIndex index.php index.html

**Add the following Types to httpd.conf.**

AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

**REstart Apache.**

---

### Post by Rush_898 on 2007-04-05
Thanks for your reply. I tried editing the http.conf file with your changes and I must have something not quite right.  I took screenshots and photobucket seems MIA so I had to use flickr.



Here is my results:

[http://www.flickr.com/photos/rush_898/447205170/](http://www.flickr.com/photos/rush_898/447205170/)



After the adds the restart told me I had a syntax problem, but I tried a few things and it didn't work.  I also removed my adds and apache restarted fine.  

Any pointers are appreciated!

---

### Post by az on 2007-04-05
First off, make sure you have the right packages installed.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I suggest you use the default LAMP stack which is apache2, php5 and mysql 5.  Make sure you remove all apache (not apache2) packages, and all php4 packages.  

Install the LAMP stack like this:

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

and take it from there.

---

