---
title: "PHP Issue?"
date: 2007-03-23
forum: Server Platforms
---

### Post by exp0zed on 2007-03-23
Not really sure exactly where this goes but I'll assume the mods will take care of it. 

I'm having a extremely weird issue, apparently my webserver will load HTML (1/'2 second) pages extremely fast but with PHP (45seconds) pages it has an issue and loads them slow. Anyone have any idea about why it might be doing this or need anymore information let me know.

Thanks

---

### Post by conjur3r on 2007-03-23
Try creating a simple PHP page with the following contents and then point your browser to the new file.  Is it quick or does it still take 45s?

<?php
echo "hi there!";
?>

---

### Post by exp0zed on 2007-03-23
> **conjur3r said:**
> Try creating a simple PHP page with the following contents and then point your browser to the new file.  Is it quick or does it still take 45s?

<?php
echo "hi there!";
?>

Nope, It's super fast. So I think it might have something to do with my MySQL. Did a little bit of research on google and found out very little. Anyone else experience the same things?

EDIT: Also, anyone know how to edit the (phpmyadmin) MySQL variables, because I think it might have something to do with it.

---

### Post by exp0zed on 2007-03-23
Still haven't figured anything out yet and it's still slower than ever.

Heres what I know:

Its caused by the MySQL somehow. Regular PHP pages load fine, but any pages that has to access the SQL database it takes FOREVER.

Any idea?

Oh yeah, how can I edit the MySQL variables?

---

### Post by tturrisi on 2007-03-23
You don't know yet that thye mysql vars are the cause of this issue.  Post one of your php-mysql scripts that take 45 seconds to load.  (w/out your db connect password of course!)  The php code you are using could be faulty or the mysql statements could be memory drains. You can also use phpmyadmin to dump (backup-export) the db and table structure as a sql file.  Post that as well.  This way we can see the db structure, table types and vars.

---

### Post by exp0zed on 2007-03-24
Well the scripts aren't mine and they use to load fine on a previous server. It's [Wordpress]("http://wordpress.org/") and [ SMF forums]("http://simplemachine.org/"). Basically any script that accesses the database is extremely slow.

---

### Post by conjur3r on 2007-03-24
The configuration file for phpmyadmin can be found in config.inc.php in the phpmyadmin folder.

Is it slow whilst using phpmyadmin as well?  Is it every single database call interactive page?  If it appears to be, have a look for some mysql logs.  Not exactly sure where it's kept but try /var/log first.

Has it always been slow or did it become slow?  Try to recall what happened when this started.  Did you change mysql (the db server) configuration at all?  Did you change your hostname?

---

### Post by exp0zed on 2007-03-25
It's always been slow on this server, it wasnt slow on the last server I had..but the odd thing is this specs of the server are greatly improved. ALSO, I messed something up with the database so I just purged it, and now I'm trying to reinstall it...getting an odd message.

> 
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl
  mysql-client-5.0
Suggested packages:
  dbishell
Recommended packages:
  mailx
The following NEW packages will be installed:
  libdbd-mysql-perl libdbi-perl libmysqlclient15-dev libnet-daemon-perl
  libplrpc-perl mysql-client-5.0 mysql-server-5.0
0 upgraded, 7 newly installed, 0 to remove and 1 not upgraded.
Need to get 6983kB/34.6MB of archives.
After unpacking 83.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
[b]Err [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper/main libnet-daemon-perl 0.38-1
  Temporary failure resolving 'de.archive.ubuntu.com'[/b]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libmysqlclient15-dev 5.0.22-0ubuntu6.06.2
  Temporary failure resolving 'security.ubuntu.com'
Err [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper/main libplrpc-perl 0.2017-1
  Temporary failure resolving 'de.archive.ubuntu.com'
0% [Connecting to de.archive.ubuntu.com]


Those are the lines I'm worried about...not too sure why it cant connect.

---

### Post by chartman on 2007-05-03
Hello exp0zed. 
I am having the same problem: VERY slow web pages when php5 and mysqld is used. Also.. your odd messages look familiar as well.
Did you find a solution to the problem?

---

