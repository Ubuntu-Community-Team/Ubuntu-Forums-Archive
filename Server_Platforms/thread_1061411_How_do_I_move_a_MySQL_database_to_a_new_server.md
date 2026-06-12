---
title: "How do I move a MySQL database to a new server?"
date: 2009-02-05
forum: Server Platforms
---

### Post by avahi on 2009-02-05
Hi,

My old server running Ubuntu Server 8.04 just crapped out on me :( (mobo is fried)
Whatever, that entire computer has been problematic for several months now.

I got ahold of a new computer and installed all the LAMP essentials to Ubuntu Server 8.10.

I have the old server's hard drive plugged in via an IDE enclosure.

How can I move all of the MySQL databases to the new server?
I already restored the contents of /var/www.

Thanks

---

### Post by mozkill on 2009-02-05
you can restore directly from backup archives if you kept backups , then create a database of the same name, then restore from the backup file.  otherwise im not sure how to do it.

you should always make backups as a regular habit, even if the backup is to the same hard drive.

---

### Post by R.Bucky on 2009-02-06
You should be using Phpmyadmin or something equivalent. In Phpmyadmin, click on a database from your install, Export as .sql and save somewhere. When you are ready to reinstall, go to the Phpmyadmin homepage (e.g.[http://localhost/phpmyadmin](http://localhost/phpmyadmin)) and click import. Locate your file and upload. You may have to alter the max_upload value in your php.ini.

To change that file, type ```
sudo gedit /etc/php5/apache2/php.ini
``` in terminal and find the line that says something like max_upload and change it to a value that corresponds to the maximum size of your .sql file. Then restart your apache server using ```
sudo /etc/init.d/apache2 force-reload
```

---

### Post by hyper_ch on 2009-02-06
you can 

(a) stop mysql and then copy the database binaries (they are in /var/lib/mysql)
or
(b) use mysqldump to create .sql files of your databases and then restore them

---

