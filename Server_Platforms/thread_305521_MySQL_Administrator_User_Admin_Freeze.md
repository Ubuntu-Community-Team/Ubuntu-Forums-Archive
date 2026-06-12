---
title: "MySQL Administrator User Admin Freeze"
date: 2006-11-23
forum: Server Platforms
---

### Post by eric_stewart on 2006-11-23
I have the latest 5.x Ubuntu installation of MySQL.  I can add/delete/modify/view users from the CLI no problem at all but when I use the GUI, MySQL Administrator, it freezes and becomes unresponsive to the point that I have to kill the process.

I have read similar posts on the subject and tried some workarounds but I don't want a workaround!  I would rather there was a patch for the issue.  Anyone aware of one?

Thanks,

Eric
check it out  --> [www.breezy.ca](www.breezy.ca) ](*,)

---

### Post by tturrisi on 2006-11-23
I have found the best gui for sql is phpmyadmin.

---

### Post by eric_stewart on 2006-11-24
Thanks for the advice.  I am now using phpadmin in place of MySQL admin and like it a lot.

/Eric

---

### Post by tturrisi on 2006-11-24
> **eric_stewart said:**
> Thanks for the advice.  I am now using phpadmin in place of MySQL admin and like it a lot.

/Eric
be sure to avail yourself of the Export feature in phpmyadmin.  You can export (save to file) portions of or the entire database in sql format.  This is a great way to do backups and an easy way to setup the db again when reinstalling or setting up another server, just import the sql file and in a few seconds everything is setup!

---

### Post by DoorGunner on 2006-11-25
I have a how too that is awaiting approval. Version 1.2.5rc corrects all the freezes etc that are occuring in v1.1.0. This how too also provides the MySQL query browser and the MySQL Workbench GUI's. You are welcome to try it out.

----------------------------------------------------------------------

Download mysql-gui-tools-5.0r6-linux-i386.tar.gz from the mysql site. This one is for x86 you can pick what ever you need.
[http://dev.mysql.com/downloads/gui-tools/5.0.html](http://dev.mysql.com/downloads/gui-tools/5.0.html)

cd /home/your_name/Desktop

To unpack the gunzip file 
Desktop$ sudo tar --directory=/opt -xzvf mysql-gui-tools-5.0r6-linux-i386.tar.gz

Move the following desktop files so they will show up in your development area of your K-menu or G-menu
sudo mv /opt/mysql-gui-tools-5.0/MySQLAdministrator.desktop /usr/share/applications/MySQLAdministrator.desktop

sudo mv /opt/mysql-gui-tools-5.0/MySQLAdministrator.desktop /usr/share/applications/MySQLAdministrator.desktop

sudo mv /opt/mysql-gui-tools-5.0/MySQLAdministrator.desktop /usr/share/applications/MySQLAdministrator.desktop

Open the MySQL admin file
sudo gedit /usr/share/applications/MySQLAdministrator.desktop
Edit 
Categories=GTK;Database;Development;Applications
to say
Categories=GTK;Database;Development
This will ensure all of the start icons are in the same place

One last thing you need to do is to include a sim link for MySQL Query Browser. It has a tendancy to look for a socket in a different location than were mysql debian has set it.
also do a sim link for my.cnf same problem.
sudo ln -s /var/run/mysqld/mysqld.sock /tmp/mysql.sock
sudo ln -s /etc/mysql/mysql.cnf /etc/mysql.cnf

and Bobs your uncle....Enjoy

---

### Post by digeratess on 2006-11-26
DoorGunner,

I've been having the exact problem reported originally in this thread. I followed your instructions and they fixed it. One very minor note is that MySql Administrator was originally in Applications > System Tools, and after the instructions, it was in Applications > Programming. Easy enough to find and change back.

Thanks!

---

### Post by DoorGunner on 2006-11-26
glad to have helped.....

---

