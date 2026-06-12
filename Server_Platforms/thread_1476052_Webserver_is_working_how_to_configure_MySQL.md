---
title: "Webserver is working how to configure MySQL"
date: 2010-05-07
forum: Server Platforms
---

### Post by jrtboat on 2010-05-07
So in my first ever attempt at Linux (and servers) I was able to set up a working web server that is visible from outside my network and created a simple PHP page thanks to [this ]("http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/")tutorial.  I installed MySQL and have some experience with MS SQL but have no clue how to get started setting up databases and writing procedures in MySQL.  I know all the syntax about writing scripts for MySQL (assuming it's the same as SQL) but I don't know how to get started.  Do I need to be on the web server or can I do it remotely?  Is there a front end GUI that everyone uses?

---

### Post by volkswagner on 2010-05-07
For a frontend you can look into [PhpMyAdmin]("http://www.phpmyadmin.net/home_page/index.php").

You can use the command line to create, edit, or query tables.

To get into mysql provided you set a root password.  If you did not you can drop the '-p'.  I believe most installs have a blank root password.

```
mysql -u root -p
```

For more help on the command line:

```
man mysql
```

---

