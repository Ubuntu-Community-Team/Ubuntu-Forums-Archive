---
title: "Migrate Mysql 4 database to a new server with mysql 5"
date: 2007-05-24
forum: Server Platforms
---

### Post by Azzuron on 2007-05-24
Hi, we have a server that i think is redhat or fedora, that runs mysql 4.0.x. We are changing out the servers and ive installed ubuntu on the new server, and mysql-server package as well as mysql-client. the version is 5.x is it as simple as copying the data folder from the old server to the new server? will the DBMS update the files on its own? I know for sure i could just do a dump into an sql file and reimport it. this has alot of overhead though, and wouldn't be easy as we have a strange version of phpmyadmin on that server, and can only dump one database at a time. It also doesn't have the commandline client installed.

Im looking for some resources on how to do this. i've done my best to search around mysqls site for info, and i havn't seen anything, but im not a super sluth on the web either. :(

   --Dave

---

### Post by craigp84 on 2007-05-24
Hi Azzuron,

> the version is 5.x is it as simple as copying the data folder from the old server to the new server? 

Unfortunately not :( There's a few things to watch out for but most common problem seems to be the fact mysql 4 uses the latin1 char set by default whereas 5.x made the switch to UTF8. This can result in some corrupted data.

Google this, there's a few good guides out there already.

> I know for sure i could just do a dump into an sql file and reimport it.

This is the sensible way, but as above, you'll need to account for char sets.

> wouldn't be easy as we have a strange version of phpmyadmin on that server, and can only dump one database at a time.

I'd recommend doing anything as big as this from the command line. Skip the phpmyadmin.

> It also doesn't have the commandline client installed.

Easily fixed :-)

[http://www.hackszine.com/blog/archive/2007/05/mysql_database_migration_latin.html](http://www.hackszine.com/blog/archive/2007/05/mysql_database_migration_latin.html)

---

### Post by Azzuron on 2007-05-24
thanks for the info. i think this would probably work. I still don't have mysqldump or mysql on the server we are coming from though. so its tough to dump the data like that.

If i dump the data via phpmyadmin (the easiest way to get it out, even though it would take some time), the sql commands shouldn't require anything special for the char set as the insert commands can be issued without specification of the charset so it would default to utf8 when i import it, supposing the data is extracted correctly. I am hesitant to try and install mysql client tools on the server as i dont know the OS version, i just suspect, uname -a didnt tell me much it just says "linux" and the kernel version.

     --Dave

---

