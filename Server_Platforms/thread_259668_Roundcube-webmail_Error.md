---
title: "Roundcube-webmail Error"
date: 2006-09-17
forum: Server Platforms
---

### Post by atraeyu on 2006-09-17
I installed roundcube-webmail using synaptic.
Edited the two config files.

Loaded up the app and got the php error:

> DB Error in /usr/share/roundcube-webmail/program/include/rcube_db.inc (63): DB Error: connect failed

Fatal error: Call to undefined method DB_Error::query() in /usr/share/roundcube-webmail/program/include/rcube_db.inc on line 124


Looks like maybe its a dependency problem?  Not sure ... maybe pear?  Never installed pear before ..

---

### Post by dcherryholmes on 2006-10-25
I get the same error.  There's not much in /usr/share/doc/roundcube-webmail/ either.

---

### Post by lvanderree on 2007-01-17
Just installed roundcube, 

looks nice, 

What you have to do after apt-get is:

go to konsole or terminal and:
```

cd /usr/share/roundcube-webmail/config

```

there are two files (the ones you gets complains about) 

remove the .dist from their names:
```

sudo mv db.inc.php.dist db.inc.php 
sudo mv main.inc.php.dist main.inc.php

```

And of course edit them
```

gksudo gedit main.inc.php
gksudo gedit db.inc.php

```
I hope these are pretty self explainatory.

Now you are almost there, you just have to make a new database and fill it with default tabels. Depending on your choice you can find the initial database in:
```

cd /usr/share/roundcube-webmail/SQL

```

I've chosen for mysql(5). So made a new database and user with phpmyadmin and selected this file from my browser in the phpmyadmin/querywindow.php page.

Goodluck

Ps. you can find localizations in [http://sourceforge.net/project/showfiles.php?group_id=139281](http://sourceforge.net/project/showfiles.php?group_id=139281)
just copy the tar.gz to /usr/share/roundcube-webmail/program/localization and untar.gz it over there.

---

### Post by flint_ on 2008-03-28
This is an interesting error.  I have two virtuals, one has debian 4.0 and installed perfectly.  The other has Ubuntu 6.06 LTS.  It breaks on install.

Here is the difference:

**Debian GNU/Linux 4.0**

roundcube - skinnable AJAX based webmail solution for IMAP servers
roundcube-core - skinnable AJAX based webmail solution for IMAP servers
roundcube-mysql - virtual package providing MySQL dependencies for RoundCube
roundcube-pgsql - virtual package providing PostgreSQL dependencies for RoundCube
roundcube-sqlite - virtual package providing sqlite dependencies for RoundCube

Why is it that roundcube on 4.0 works out of the box but 

[B]
Ubuntu 6.06 LTS[/B]

roundcube-webmail - A browser-based multilingual AJAX-powered IMAP client

Is this package broken on the Ubuntu repositories?

Should I revert to Debian?

Regards,

Flint

---

### Post by flint_ on 2008-03-28
The difference between the Debian 4.0 and the Ubuntu 6.06 LTS turns out to be a difference in my /etc/apt/sources.list.

The trick is to set the database up.  The newer version of this program does this automatically.  To set up the database the following commands will come in useful...

On a clean mysql you do not need a password.  This works:


mysqladmin -u root -p create mydatabase

mysql roundcube < SQL/mysql.initial.sql


First, if you haven't done this already, set the root password for MySQL. You can do this by typing:


Password Set:
mysqladmin -u root password 'passwordyouwant'
or
mysql -u root -p


To login try:
mysql --user=root --password=passwordyouwant

Try:
show databases;
SHOW TABLES;
DESCRIBE 'particular_table';


At the prompt set the roundcube database password:
GRANT ALL ON roundcube.* TO roundcube@localhost IDENTIFIED BY "password4roundcube"

then go into the /config/db.inc.php and fix it to log in...

This should all be done automatically but hey...


Regards,

Flint

---

