---
title: "mysql with apache and php?"
date: 2005-02-10
forum: Server Platforms
---

### Post by Kvark on 2005-02-10
phpMyAdmin gives me this message:

cannot load mysql extension,
please check PHP Configuration
Documentation


What i have done so far is...

Got apache2, libapache2-mod-php4 and mysql-server with synaptic package manager.

Changed apache2's sites-available/default file to add an alias for a directory I can write to.

Downloaded phpMyAdmin manually and put it in that directory.

Did "/usr/bin/mysqladmin -u root password *blanked*" and put *blanked* in config.inc.php cause i saw someone suggest that in another thread.

...dunno what more to do to get it working.  :-k

---

### Post by ups on 2005-02-11
there's a php module for mysql, you need to install that. I dont remember the exact name, and I have some big upgrades running (so cant search in synaptic atm) - just search for mysql or php and see if there's something that is called php4-mysql or similar.

---

### Post by Kvark on 2005-02-11
wow it worked, thanks :D

Couldn't have guessed on a solution that is so easy cause I used only windows and dos before. This is like changing from 18th centenary cut your own firewood to 22th centenary tell robot slave to autmatically go buy foodstuffs and cook dinner. :shock:

---

### Post by dewey on 2005-02-12
Yes, I believe that with PHP5, they removed native MySQL support, so you have to add it yourself.

---

### Post by lekoya on 2006-07-21
Hi All, I have the problem with mysql. it doesnt seem to communicate with php. it gives me errors like, "Fatal error: Call to undefined function mysql_query() in /home/tseko/public_html/project/xzy/yy.php";

I have tried everything to try and solve the problem.

Thanks

---

### Post by lekoya on 2006-07-21
Hi All, I have the problem with mysql. it doesnt seem to communicate with php. it gives me errors like, "Fatal error: Call to undefined function mysql_query() in /home/tseko/public_html/project/xzy/yy.php";

I have tried everything to try and solve the problem.

Thanks

---

