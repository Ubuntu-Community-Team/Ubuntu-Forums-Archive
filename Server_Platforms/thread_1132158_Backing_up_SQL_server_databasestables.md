---
title: "Backing up SQL server databases/tables"
date: 2009-04-21
forum: Server Platforms
---

### Post by Kareeser on 2009-04-21
Hey everybody!

Just upgraded from Hardy to Intrepid, smoothest upgrade ever! I even had time left over to migrate my old backup scripts (where I'd used 7zip) to more traditional gzipped tarballs.

Aaaanyways:

My server also contains a MySQL server, and my method of backing up requires logging into the server by hand via phpMyAdmin and exporting the requisite tables from there.

However, this is very cumbersome and requires me to be present every week when I do my backup, and I was wondering if there was a way to automate this process.

I realize I could set up a cronned script to access the mysql database, but I have no clue how to go about setting something like that up. I've actually never written real scripts before, so this is fairly new to me.

I was advised at one point to backup the entire database folder on the server... I can't seem to find it now... but it also seems like a huge security risk =P

Help me out! :)

---

### Post by koenn on 2009-04-21
make your backup script run mysqldump. It creates sql scripts that you can use to rebuild your database and/or insert the data back in to it. It's a pretty generic way to backup databases, and works across systems (eg you can use the output to create a new database on another host)



man mysqldump or [http://users.telenet.be/mydotcom/howto/linux/backups.htm#mysql](http://users.telenet.be/mydotcom/howto/linux/backups.htm#mysql)

---

### Post by xkaliburx on 2009-04-21
I've been using this script for a while now.  It creates daily, weekly, monthly and year folders, keeps a 5 day rolling daily, moves the end of week to weekly, keeps 5 of those, etc.  Great, great app....

[http://sourceforge.net/projects/automysqlbackup](http://sourceforge.net/projects/automysqlbackup)

---

### Post by Kareeser on 2009-04-24
Thank you to both of you!

I've investigated the use of mysqldump, and it works perfectly! Now I can sit back knowing that my server is being backed up regularly :)

---

