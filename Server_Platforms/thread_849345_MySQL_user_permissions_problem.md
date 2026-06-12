---
title: "MySQL user permissions problem"
date: 2008-07-04
forum: Server Platforms
---

### Post by philo23 on 2008-07-04
Well i've been using Fedora for a while, but i decided to move back to ubuntu so i exported my MySQL db from the Fedora server, then i imported it back into the new ubuntu web server i've got, but i noticed once i dumped the file back, i had exported the mysql and information_schema table and it errored, now i thought nothing of it at first, but then i noticed that none of my web apps could login to my MySQL server, unless they used the mysql root user, which i didnt really want to use for a production enviroment atal. so i'm wondering ether:

1) How can i completely uninstall and remove all tables in the database (when i just do apt-get remove mysql-server it keeps the tables some where...)
or
2) How can i fix the mysql user permissions?

Thanks in advance for anyone willing to help, you'll save me alot of bother of completely reinstalling Ubuntu when i've pretty much only just installed it.

---

### Post by James79 on 2008-07-06
Do you still have access to the old database?

If so, I would dump the mysql.users table to a flat file, and import it into your new database.

At the original server:

> mysqldump -uroot -p --databases mysql --tables user --compact --no-create-info > mysql.users.sql

Copy the resulting sql file to the new server, and issue this command:

> mysql -u root -p < mysql.users.sql

Failing that, you'll pretty much have to recreate them by hand or using whatever tool created your users originally.

Hope that helps.

[edit] be warned that this will also "copy over" your root user and password from your original install. If that is unacceptable, simply edit the file and remove the user in question.

---

### Post by philo23 on 2008-07-09
thats not the problem i've got everything moved over and it isnt a user table as in like a custom one for a site i have, its *the* MySQL user table it self. and even the root mysql user will not allow me to edit the mysql database or the information_schema database.

---

