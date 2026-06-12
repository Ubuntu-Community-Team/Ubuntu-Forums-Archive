---
title: "apache include_path woes with dapper upgrade"
date: 2006-05-26
forum: Server Platforms
---

### Post by goneskiing on 2006-05-26
I did a clean install of dapper from breezy and now my php front_controller program is giving me this error:

Warning: require(/var/test/front_controller.php) [function.require]: failed to open stream: Permission denied in /var/www/test on line 7

Fatal error: require() [function.require]: Failed opening required '/var/test/front_controller.php' (include_path='.:/usr/share/php') in /var/www/test on line 7


Perhaps my clean install wiped out a setting I had somewhere or a hidden .htaccess file but does anyone know why I'm getting this problem ?   From google search I see I can inlcude a .htaccess file in the doc root specifying the out of root directory where my php programs reside - is that the right way ?  Thks for any help.

---

