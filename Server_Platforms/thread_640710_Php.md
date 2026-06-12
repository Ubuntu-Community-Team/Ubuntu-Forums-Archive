---
title: "Php"
date: 2007-12-14
forum: Server Platforms
---

### Post by dacool25 on 2007-12-14
Hi there Guys,

For some reason I can't get php to work.  I just unzipped phpmyadmin to my web directory and when trying to pull up any php file i just get the code in my browser.

PHP5 is installed, which is what is confusing me.  Is there a service under /etc/init.d that i need to start?

Thanks!

---

### Post by bnuytten on 2007-12-15
Are you using PHP in standalone mode or in combination with Apache? In the latter case, make sure you have libapache2-mod-php5 installed.

---

### Post by dacool25 on 2007-12-15
With apache.  But i have ISPConfig installed. Not sure if that would have anything to do with it.

I also already have libapache2-mod-php5 installed

---

### Post by bnuytten on 2007-12-16
Make sure your test file has the php extention. If the file is named test.html it will (by default) not be parsed by PHP. Simply rename it to test.php and it should work. You can have html files parsed by PHP too if you want, but that is beyond the scope of this issue.

Also check if you have the PHP5 module for Apache enabled. If they are not enabled, do not create manual symlinks but use "sudo a2enmod php5".```

ls -l /etc/apache2/mods-enabled/php5*
lrwxrwxrwx 1 root root 27 2007-11-27 20:44 /etc/apache2/mods-enabled/php5.conf -> ../mods-available/php5.conf
lrwxrwxrwx 1 root root 27 2007-11-27 20:44 /etc/apache2/mods-enabled/php5.load -> ../mods-available/php5.load
sudo a2enmod php5
This module is already enabled!

```

---

