---
title: "How to reverse-engineer a MySQL database with Visio"
date: 2008-06-28
forum: Server Platforms
---

### Post by promodus on 2008-06-28
If you're like myself and you're working with a database you're wishing to inject data into, visualizing the structure can be an important time-saving asset.

I'm on a multi-platform environment. I would prefer to have an open source visio tool that can reverse engineer a database similar to visio. If anyone knows of one, or a similar process please post about it.

I have a MySQL Database, and a Windows XP host running Visio.

1. Enable your MySQL to listen for network connections.
2. Allow privileges for your MySQL for the XP client to connect
3. Install the MySQL ODBC connector
[http://download.softagency.net/MySQL/Downloads/Connector-Net/]("http://download.softagency.net/MySQL/Downloads/Connector-Net/")
4. Create the ODBC connector
On the windows machine:
Control Panel &#8594; Administrative Tools &#8594; Data Source (ODBC)
Click on System DSN, then click Add...
Choose MySQL ODBC 5.1 Driver

From there add the [COLOR="DarkGreen"]Data Source name[/COLOR], Can be anything you want.
Then add the server, user, pass & database info.

5. Open up Visio
6. File &#8594; New &#8594; Software and Database &#8594; Database Model Diagram
6. From the menu, select Database &#8594; Reverse Engineer
7. Select the [COLOR="DarkGreen"]Data Source name[/COLOR]
8. Click Next >
9. Enter your password, and click OK

10. Select all tables or views you wish to reverse engineer

11. Click "Yes, add the shapes to the current page."
12. Click Finish.

If you're prompted about a certain error, it's usually minor. keep clicking ok, and you'll have the tables now diagrammed. The relationships will take some work.

---

### Post by yogensha on 2008-06-30
This is a great idea, I didn't know Visio could do this.  I recently searched around for an open source utility that could do this, but none that I found were capable of "reverse engineering" the database schema.

It didn't occur to me to use a windows tool via ODBC.  Visio is quite pricey, and I don't need 90% of its features.  Do you know of any free or inexpensive windows tools that can do this?

---

### Post by promodus on 2008-07-02
> 
It didn't occur to me to use a windows tool via ODBC.  Visio is quite pricey, and I don't need 90% of its features.  Do you know of any free or inexpensive windows tools that can do this?

[http://www.visual-paradigm.com/product/dbva/demos/dbmodeling/dbtoerd.jsp](http://www.visual-paradigm.com/product/dbva/demos/dbmodeling/dbtoerd.jsp)

Uhm, MySQL workbench will do it, but the commercial version to do a live database is $99.
[http://www.mysql.com/products/workbench/features.html](http://www.mysql.com/products/workbench/features.html)

Well I'll bump the thread, maybe someone out there knows of some open source tools to reverse model databases.

---

### Post by dogoku on 2009-05-08
Here's a rather simple way you can create EER diagram from existing dbs

It requires the MySQL Workbench, mentioned above

And it requires any program that can dump your mysql DB. Even phpMyAdmin can do that. 
(But i used Navicat, which is a very nice DB managment program. You can get it at [http://www.navicat.com/html/index.php/en/products/navicat_mysql/mysql_overview.html](http://www.navicat.com/html/index.php/en/products/navicat_mysql/mysql_overview.html) .Of course comes for Linux too)

Anyway once u got your raw sql dump of your DB (the .sql script) just open MySQL Workbench, choose import and watch it do all the work for ya
(I wouldnt suggest choosing to auto arrange, once the import is done, as it will just pop all tables at the same place in the diagram :P)


Hope i helped (sorry i bumped a one-year old thread, but google popped it up, and when i read the last post, i knew i had to help :) )

---

### Post by yogensha on 2009-05-08
Cool, thanks for the tip!

---

### Post by immeëmosol on 2010-10-21
i know that by now it is possible to see the tables in a graphical manner in phpmyadmin isn't that noice? :)

---

