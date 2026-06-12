---
title: "ununtu to windows with mysql"
date: 2011-05-13
forum: Server Platforms
---

### Post by nkarthik on 2011-05-13
hi guys i want connect ubuntu server to windows and retrive mysql from windows

---

### Post by volkswagner on 2011-05-13
Please explain.

Do you want Ubuntu to query/insert data into a windows box running MySql?

Or do you want to migrate from Windows running MySql and move it to your Ubuntu server?

---

### Post by nkarthik on 2011-05-13
> **nkarthik said:**
> hi guys i want connect ubuntu server to windows and retrive mysql from windows
thanks for response 
actually i want acess database (mysql) from windows xp through ubuntu server
I want Ubuntu to query/insert data into a ubuntu box running MySql

---

### Post by SeijiSensei on 2011-05-13
I don't think that adequately answers the question either.

If you mean you want to run a MySQL server on an Ubuntu box, and access it from an application running on Windows, you need the install the MySQL [ODBC connector]("http://dev.mysql.com/downloads/connector/odbc/") for Windows.  Then you can define a Data Source in the Control Panel that you can point to from ODBC-aware applications like Access or Excel.

If you mean you want to connect to the Ubuntu server and run the command-line mysql client remotely, use [putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") to SSH into the Ubuntu server.

---

### Post by volkswagner on 2011-05-13
Without any specific criteria, my first two suggestions would be to use Putty to ssh into the Ubuntu server and administer Mysql.  You may also be interested in [PhpMyadmin]("http://www.phpmyadmin.net").

I have not used this yet, you may be interested in [MySQL Workbench]("http://dev.mysql.com/doc/workbench/en/index.html").

---

### Post by nkarthik on 2011-05-13
how to install the 
**Connector/ODBC**

in ubuntu pls give steps.I am using 32-bit.and which package to download.
and i have also install mysql workbench whe i try to connect another system it is showing 
Lost connection to MySQL server at 'reading initial communication packet', system error: 113
pls help

---

### Post by volkswagner on 2011-05-13
> **nkarthik said:**
> how to install the 
**Connector/ODBC**

in ubuntu pls give steps.I am using 32-bit.and which package to download.
and i have also install mysql workbench whe i try to connect another system it is showing 
Lost connection to MySQL server at 'reading initial communication packet', system error: 113
pls help

Have you enabled remote connections in /etc/mysql/my.cnf?

```
sudo nano /etc/mysql/my.cnf
```

look for line:
```
bind-address           = 127.0.0.1
```

an unsecure method would be to just comment out the line.  For more secure mode, you can add your local network range.

[Link for more info]("http://ubuntuforums.org/showpost.php?p=6045337&postcount=2").

---

### Post by SeijiSensei on 2011-05-13
> **nkarthik said:**
> how to install the 
**Connector/ODBC**

Did you miss the link in the middle of the page I linked to that reads "[Connector/ODBC Documentation]("http://dev.mysql.com/doc/refman/5.1/en/connector-odbc.html")"?

---

### Post by wangkeit on 2011-05-14
> **nkarthik said:**
> hi guys i want connect ubuntu server to windows and retrive mysql from windows
share with samba server. oh y if you want your web uploud then you should choose a cheap hosting, on [http://www.hostingfest.com](http://www.hostingfest.com).
I share the data with the configuration between wiondows and linux

---

