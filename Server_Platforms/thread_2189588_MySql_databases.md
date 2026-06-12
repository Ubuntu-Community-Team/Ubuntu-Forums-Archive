---
title: "MySql databases"
date: 2013-11-23
forum: Server Platforms
---

### Post by salmendar on 2013-11-23
i had a pc in which i did all my personal php development that  fried(electrical problems). now i have a lot of db in my hard disk, i put it as slave in my server... it has all the previous DB's and backups but in the old hard disk which i want to move to my sql database of server.... how can i do that .

if i move the folder only the database name comes while the tables are just missing... please tell me how to do this.


ps. both hard disk are on the same mechine and i want only one folder to work.

---

### Post by SeijiSensei on 2013-11-23
You say your old drive has "backups".  Were they created with mysqldump?  If so, you can [read those files into the new server]("http://www.tecmint.com/mysql-backup-and-restore-commands-for-database-administration/") with the mysql command-line client.  

I've also had success with getting MySQL to read an existing server instance that was stored in /var/lib/mysql.  You can give that a try by first moving the current mysql directory to a safe location then creating a symbolic link to the old one.  Let's suppose your old drive is mounted on /mnt, so that the old MySQL instance is stored in /mnt/var/lib/mysql.  Then you can try:

```

sudo service mysql stop
cd /var/lib
sudo mv mysql mysql.new
sudo ln -s /mnt/var/lib/mysql
sudo service mysql start

```

In practice you need to replace /mnt with whatever mount point you use to access the old drive.

Does that work?

---

### Post by salmendar on 2013-11-24
the rpoblem is the they were not dumped... that is the main issue. i didnt get the time to dump them, the system fried .

---

### Post by SeijiSensei on 2013-11-26
Did you try pointing the MySQL server at the instance on the old disk like I described?

---

