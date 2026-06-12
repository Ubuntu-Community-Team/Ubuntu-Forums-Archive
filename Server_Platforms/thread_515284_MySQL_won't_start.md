---
title: "MySQL won't start"
date: 2007-08-01
forum: Server Platforms
---

### Post by CLI-Linux on 2007-08-01
So, I was editing stuff in Wordpress when all of a sudden I get locked out of the blog altogether.  Having a bad feeling, I checked phpMyAdmin which was working to some extent, but had a few problems along the way.  Then, trying to restart the MySQL daemon, I get nothing.  Stops, but won't start.

Tried removing and reinstalling MySQL 5.0, but with no luck.  My only guess is that there's an error the initscript is encountering when trying to start the daemon.

Any help would be great.  Thanks!  And need info, just ask.

***EDIT***
Got this error on startup:
```

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

A re-install of MySQL finally did the trick.  Don't know what I did differently the second time around but now it all works.  Found out later that one of the tables in Wordpress had been corrupted.  I repaired it and now everything's working fine again.

---

### Post by jpeddicord on 2007-08-03
Weird.. the same happened to me not too long ago. MySQL refused to restart, but a complete system reboot did the trick.

Jacob

---

### Post by CLI-Linux on 2007-08-04
I tried a system reboot, but no luck.  I'm not really sure how it happened to be honest.  All of a sudden, I think Wordpress hiccuped and spat a bad query to MySQL which corrupted a table entry.  Long story short, I uninstalled all parts of MySQL including phpmyadmin and did a reinstall: 

```
sudo apt-get install mysql-server
```

After that, everything came back up.  I had to run a repair function on the wp_options table in MySQL, but that didn't take long and it repaired successfully.  Also, the reason I found the table error came from a re-import of the wordpress database.  The error popped up and from there I figured out what went wrong from the beginning.  Feels good to be able to fix something like this on my own now. :)

---

