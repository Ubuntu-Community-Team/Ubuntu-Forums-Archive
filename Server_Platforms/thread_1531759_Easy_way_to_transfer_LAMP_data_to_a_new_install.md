---
title: "Easy way to transfer LAMP data to a new install?"
date: 2010-07-15
forum: Server Platforms
---

### Post by SoftwareExplorer on 2010-07-15
Is there an easy way to transfer Webserver data from one ubuntu install to a new one? I know I'll need to get the stuff in /var/www and (somehow) the Mysql data, but are there files elsewhere to get? Or is there a better way than trying to copy all the various files?

---

### Post by kevin11951 on 2010-07-15
You can use phpMyAdmin to export your databases, and then import them again on the new servers with phpMyAdmin as well.

---

### Post by SoftwareExplorer on 2010-07-15
So, in my searching, I found out that you can move the mysql data with something like mysqldump -uroot -p -A -x > file.sql on the old machine and then mysql -uroot -p < file.sql on the new machine. Kevin11951, thanks for the phpMyAdmin advice, I think it would work in place of the mysqldump. The other things I had to do:

I copied over /var/www and made sure it and everything in it was owned by www-data. I also copied over /etc/apache2, replacing the default settings the new machine had. The thing that took the longest to figure out is that I had to change /etc/hosts to have the same name as the previous install or pictures wouldn't load in wordpress.

---

