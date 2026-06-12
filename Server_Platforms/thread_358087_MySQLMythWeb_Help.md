---
title: "MySQL/MythWeb Help"
date: 2007-02-10
forum: Server Platforms
---

### Post by Kev1729 on 2007-02-10
Right so, have mythtv with mythweb installed on my mythtv computer, which is connected to my other computer with a x-over cable, which is in turn connected to my router, which is connected to all my other computers and ultimately the Internet.

From my main box i can access mythweb by going to 192.168.2.2 (the main box is 192.168.2.1), but i can't access the mythweb that is installed into my main box (which is trying to connect to my mythtv box), if you follow.

Basically, i can't access my mysql installation from a different box, and i really have no idea what or how to configure it to work.

When i try to just do mysql_connect('192.168.2.2', 'etc', 'etc'); in PHP i get: "Warning: mysql_connect(): Lost connection to MySQL server during query in /usr/share/mythtv/mythweb/test.php on line 3
Lost connection to MySQL server during query"

Please help me!

:)

---

### Post by Kev1729 on 2007-02-11
*Hangs head in shame*

It seems i just never created a MySQL user to be allowed to access the database.

New problem:

When i access the MythWeb with 192.168.0.5 (which connects to 192.168.2.2) the page takes ages to load, then spits out a whole load of these types of error messages:

Error at /opt/lampp/htdocs/mythweb/includes/programs.php, line 330:
date() expects parameter 2 to be long, string given

Other pages work fine though....

Now, before that it said there was a protocol mismatch, which i just forced up to match, could this be the problem?  Also, the MythWeb installed on the MythTV computer works fine and never said there was a protocol mismatch.

I tried using the mythweb package with apt-get, but that just downloaded PHP and MySQL and messed up my lampp install.  I am also using the latest mythweb from the MythTV site so i don't think there is any difference.

:)

---

