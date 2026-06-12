---
title: "Wordpress installation on LAMP"
date: 2013-11-30
forum: Server Platforms
---

### Post by sw1ayfe on 2013-11-30
I'm running Lubuntu 13.10 on a Samsung NC10 plus netbook. For the record it's been rock solid so far.

I've managed to setup LAMP. Have phpmyadmin working.

Attempting to install Wordpress so I can run as a test version before implementing changes to my live site. I already stuffed something yesterday testing out child theme. I still don't quite get it but I'll get there. This meant the site was down all day and I don't want that to happen again in future.

Following these instructions [https://help.ubuntu.com/13.04/serverguide/wordpress.html](https://help.ubuntu.com/13.04/serverguide/wordpress.html) I seem to have it all going well until the last bit of code:
```
[COLOR=#333333][FONT=monospace]cat wordpress.sql | sudo mysql --defaults-extra-file=/etc/mysql/debian.cnf[/FONT][/COLOR]
```

Firstly it said there was "no such file or directory"

So I then after following a few variations via [http://ubuntuforums.org/archive/index.php/t-824277.html](http://ubuntuforums.org/archive/index.php/t-824277.html) specifically
```
[COLOR=#000000][FONT=verdana]mysqldump -u username -p wordpress > wordpress.sql[/FONT][/COLOR]
```

I managed to get there to be no error. But I'm not sure if that was the only piece of code I should have used?

So when I now try to get into localhost/blog/wp-admin/install.php I get "Error establishing a database connection"


This is all after a previous setup of LAMP confused the out of me so I just removed and purged all the files and started again. Getting so close to working it out mwahaha. Would really appreciate any help anyone can offer me.

EDIT: Just as cautionary I also just ran
```
mysql -u username -p wordpress < wordpress.sql
```
and restarted apache2 and meh, same error

---

### Post by rackit on 2013-11-30
I always create a user in phpmyadmin and assign them a database with the same username with all permissions except grant - then I set the password by hand. The wp-config.php has the settings needed to connect to the database if the wordpress "install wizard" doesn't ask you for any database info. If you dont have a wp-settings.php file, cp wp-config.new.php wp-config.php and there you go.
```
define('DB_NAME', 'your db name');    // The name of the database
define('DB_USER', 'your db username');     // Your MySQL username
define('DB_PASSWORD', 'your db username password'); // ...and password
define('DB_HOST', 'localhost');    // 99% chance you won't need to change this value
```

---

### Post by sw1ayfe on 2013-11-30
Awesome matey thank you. I did not know it actually did that too. Was really doing me in all the back and forwards and I couldn't visually imagine the difference between my hosted server and this. All setup now after starting it clean.

Now just to work out how to do the backed up test version of a live wordpress site. Eek

---

### Post by rackit on 2013-11-30
I do a full db dump from phpmyadmin and then pull it back in to the working server. You can do the same from mysql workbench... just different vernacular.

---

