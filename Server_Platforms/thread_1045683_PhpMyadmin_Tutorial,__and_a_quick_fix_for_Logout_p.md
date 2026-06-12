---
title: "PhpMyadmin Tutorial,  and a quick fix for Logout problem"
date: 2009-01-20
forum: Server Platforms
---

### Post by Lukasz Tarkowski on 2009-01-20
1 Download phpMyAdmin 2.11.9.4 Utf 8 Version!
2 Rename phpMyadmin 2.11.9.4 to PhpMyAdmin
3 Press alt-f2,  then gksudo nautilus /var/www/
4 Copy phpMyAdmin to /var/www/ you opened up with nautilus!
5 Go to the setup [http://your](http://your) webserver/sripts/setup.php
6 Click add server and start configuring! Add Usersnames and Passwords
7 You can configure upload and download as well,  they both should be  /var/www/  
8 Click download config.inc.php and save it to documents.
9 Press alt-f2,  then typ gksudo nautilus /var/www/
10 From the documents copy into /var/www/phpmyadmin/
11 Open up config.inc.php
12 Add this //$cfg['Servers'][$i]['LogoutURL'] = 'http://rukasuzu.00-com.info/phpmyadmin/';

Remember never remove **"//"** from Cfg logout url

---

