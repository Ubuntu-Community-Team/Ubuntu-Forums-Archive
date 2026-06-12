---
title: "Server install shared for dual boot"
date: 2010-03-29
forum: Server Platforms
---

### Post by gavintlgold on 2010-03-29
I'm running a small server with a forums from my computer that I don't expect to get very much traffic on. I dual boot Ubuntu (Lucid) and Windows 7, because I play computer games on the Windows side.

I would like to be able to use Ubuntu for everything except gaming so was wondering if there would be a way for my Windows installation of Apache/PHP/mySQL to use all the same files as my Ubuntu installation so that the website would be accessible regardless of which OS i'm currently booted into.

I can understand how I could set my default Ubuntu Apache directory to my Windows apache directory to share the actual web pages, but I'm unsure if it would be possible to do the same thing with the mySQL databases.

Has anyone had any experience with this or have any ideas about sharing a single database installation with multiple server installs (not ever running concurrently)?

---

### Post by s_ø on 2010-03-30
Hi.
I dont think you can share the database files between ubuntu/windows directly. As I understand the MySQL setup you need the database files in a specific location.
The format of the files is the same, so you could setup a script that copied the files from ubuntu to windows when you stop the mysql server. See this page [http://articles.techrepublic.com.com/5100-10878_11-5259660.html](http://articles.techrepublic.com.com/5100-10878_11-5259660.html)
But windows dont support other filesystems than FAT and NTFS, so it would be a problem the other way.

One option could be to make a ntfs partition and mount it at /var/lib/mysql in ubuntu. You would then need to mount it at mysql\data in windows (if thats even possible). I have no idea about security and data integrity implications. But it would be funny if it was possible.
MySQL installation layout [http://dev.mysql.com/doc/refman/5.5/en/installation-layouts.html](http://dev.mysql.com/doc/refman/5.5/en/installation-layouts.html)

Ill probably try it myself tonight.

---

### Post by gavintlgold on 2010-03-30
What if I made a symlink to the windows mysql data folder in Ubuntu and made sure the windows partition was always mounted?

---

### Post by s_ø on 2010-03-30
Tried to symlink but it didnt work.
I cp the /var/lib/mysql to my desktop and made symlink in its place. The server couldnt start. Tried with subdirs (the actual DBs) but same result.
I then mounted the mysql folder from my desktop at /var/lib/mysql and it worked.
Now im gonna setup the server on my windows and try it out.

---

### Post by s_ø on 2010-03-30
Ok.
I got it up and running. MySQL on windows/ubuntu dualboot share the same database files.
It has some small quirks that I need to fix, but it is working.

I setup a separate NTFS partition.
Then copy the contents of /var/lib/mysql to the new partition.
Then delete contents of /var/lib/mysql.
Then mount the new NTFS partition at /var/lib/mysql
```
sudo mount /dev/sdc4 /var/lib/mysql -o uid=mysql,gid=mysql,umask=0077
```

in windows locate my.ini.
Change datadir to the NTFS partition holding the database files.

Some problems.
The '$RECYCLE.BIN' and 'System Volume Information' are two brand new databases.
I used the data directory from the windows install, so i was missing the user debian-sys-maint.
Create the user debian-sys-maint. The password for debian-sys-maint can be found in /etx/mysql/debian.cnf.
Then```

GRANT SHUTDOWN ON *.* TO 'debian-sys-maint'@'localhost';
GRANT SELECT ON `mysql`.`user` TO 'debian-sys-maint'@'localhost';
```

It would be more clean if you only share one database. Remember windows is case-insensitive and linux is case-sensitive so keep all names in lowercase.

Now im off to bed - its 02.20 my time.
__

---

### Post by s_ø on 2010-04-01
If you are still interested here is a little howto share MySQL in dual boot.
MySQL uses the same fileformats across platforms. So all you need is to share the data directory. One problem is that the data directory need to have mysql as owner and group in ubuntu.

Install and setup MySQL on both systems.
The default LAMP install on ubuntu wont allow root login without password.
A fresh install of WampServer on windows is setup so PHPMyAdmin will use config authentification. This should be set to cookie.

Stop the mysql server if it is running.
```
sudo service mysql stop
```Make a new NTFS partition. Mine is sdc4 - substitute with your own in following examples.
Backup your mysql data.
```
sudo cp /var/lib/mysql /var/lib/mysql_backup -r
```Move the mysql data directory from Ubuntu to the new partition.
```
sudo mv /var/lib/mysql /dev/sdc4/mysql_data
```Make a new mysql directory
```
sudo mkdir /var/lib/mysql
```Now mount the NTFS partition at /var/lib/mysql. Its important to set owner, group and permissions.
```
sudo mount /dev/sdc4 /var/lib/mysql -t ntfs-3g -o uid=mysql,gid=mysql,umask=0077
```To automount on boot.
Find the partition UUID.
```
ls -l /dev/disk/by-uuid
```should give something like this.
```
lrwxrwxrwx 1 root root 10 2010-04-01 09:08 **615A3F5877E43C1C** -> ../../sdc4
```Edit your /etc/fstab file.
```
sudo nano /etc/fstab
```copy the following line at the end of your fstab file
```
UUID=**615A3F5877E43C1C** /var/lib/mysql ntfs-3g uid=mysql,gid=mysql,umask=0077,locale=da_DK.utf8  0  0
```Substitute 'locale=da_DK.utf8' with your own. To find your locale
```
locale -a
```Change the 'datadir' path in /etc/mysql/my.cnf to point to /var/lib/mysql/mysql_data
```
sudo nano /etc/mysql/my.cnf
```Start the mysql server and test it.
```
sudo service mysql start
```Now edit the windows config file. You can do it from Ubuntu if you mount the windows partition.
```
sudo nano /path-to-windows-partition/path-to-mysql-directory/my.ini
```in my case the path ws '/media/Windows/wamp/bin/mysql/mysql5.1.36/my.ini'
Set 'datadir' to 'drive-letter/mysql_data' in my case it was e:/mysql_data.

Boot windows and test.

---

### Post by gavintlgold on 2010-04-21
I've just got the time to go over your tutorial and I've noticed a small error so far: cp doesn't handle directory copying by default so it needs -r.

---

