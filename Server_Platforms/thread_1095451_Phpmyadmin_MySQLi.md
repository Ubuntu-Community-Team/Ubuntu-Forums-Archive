---
title: "Phpmyadmin MySQLi"
date: 2009-03-13
forum: Server Platforms
---

### Post by Banj007 on 2009-03-13
I've got my web server up and running on an ubuntu server, Apache works fine and until recently phpmyadmin only cried about libmcrypt which I installed. Now I get 'cannot load mysqli' error. I've searched all over aptitude for a mysqli extension for php, but to no avail. So, thinking it was already installed i added to php.ini: "extension=php_mysqli.so" and "extension=php_mysql.so" for good measure and rebooted the server to make sure php read its config and loaded the files but that also did nothing. I'm at a wall here as searching google for "libmysqli ubuntu" and the like hasn't solved my problem like it did for mcrypt. Any advice would be appreciated.

---

### Post by mrsteveman1 on 2009-03-14
Mysqli is part of PHP since 5.3, so make sure PHP is correctly installed. Also make sure php5-mysql is installed, maybe force reinstall it even if it already is.

---

### Post by Banj007 on 2009-03-17
yeah.. those are all installed so I'll force reinstall them and edit this post in a day or so when I've got the time. Thanks for the info.
---edit---
I reinstalled ubuntu server (got a new box recently) and the only difference is I no longer use libmcrypt but now phpmyadmin works... o_O

---

### Post by R4VI on 2012-07-11
Thanks Banj007, I too had the same problem. Just forgot to install php5-mysql. Did it and Yipee!! No Error...

---

