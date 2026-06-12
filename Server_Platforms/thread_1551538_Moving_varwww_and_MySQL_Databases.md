---
title: "Moving var/www and MySQL Databases"
date: 2010-08-12
forum: Server Platforms
---

### Post by wombat613 on 2010-08-12
Quick searches did not bring forth any standard solution.

I have installed Ubuntu Server 10 (x64) using LVM with two disks (this is a Virtual Machine on VMWare ESXi4) 

During install I selected only disk 1, and LVM guided Installation
Added LAMP and SSH



Server gives only a text mode configuration, great if you are a linux guru, but I am not so it took a bit to find a stripped down GUI.  None could be found but I did the following:
   
   apt-get install xorg gdm gnome-core    (minimal Gnome install)
   apt-get install gnome-system-tools       (users and *****s, time)
   apt-get install gnome-network-admin    (network config)
   apt-get install update-notifier                (updates)
apt-get install gparted (disks)
 apt-get install open-vm-tools                (vmware)

   apt-get install joe                                 (editor)


<aside this would make a great virtual appliance in my opinion, the bare minimal to configure a system, no Open Office, no Games etc etc>

Now for the second disk :

For our Disaster recovery we use Symantec Ghost to copy the System Partitions.  In Windows C: drive, and I put apache and mysql on a second disk the W: drive.

I have created a similar system with Ubuntu, now I wish to move the var/www directory to sda1, and the databases from MySQL.  



Any insight on Ghosting and restoring the system partition would also be appreciated.

Thanks for any insight.  Take two CPU seconds out of petty cash.
Wombat

---

### Post by koenn on 2010-08-12
you don't move those directories.
In stead, you mount the disk in question to a directory (mount point) eg /srv, and you configure the software to use (subdirectories in) /srv, say /srv/www and /srv/mysql

for apache, you need to edit the document root and directory definitions of the applicable sites, in /etc/apache/sites-available

for mysql, you set the location of the databases in /etc/mysql/my.conf
you may want to copy the contents of the current datadir.
also, mind that you get the ownership and permissions on the new directories correct.

---

### Post by wombat613 on 2010-08-12
OK, but not granular enough for me.  I am ok with Linux, but far from an expert.  Secondly I need to document as part of my job, so if my boss wishes to repeat what I have done, he needs it step for step.

Since this is my first time with lvm2, even that is new to me.

On second Drive, I would assume (so far without looking) using 
GParted - device /dev/sdb
Device - new partition table

/dev/sba has it as extended thenn lvm2 but I can not create that

should I create a ext2 partition (ext3 ext4?)

[edit]

First mistake GParted does not do LVM, apt-get install system-config-lvm

[edit 2]

From LVM management, created a new volume ***** Web_MySQL using the full sba

Created a new Logical Volume EXT4, mounted as /web

Now copy over /var/www
edit /etc/apache2/sites-available/default



then edit which files/lines 

I know enough linux to be dangerous, which is why I prefer to confirm before moving on.

Wombat

---

### Post by wombat613 on 2010-08-12
No go for MySQL

following several web pages, in short
Shut down MySQL
Create new directory give ownership to mysql
copy files over
edit my.cnf
restart MySQL

Anytime I set my.cnf to use the new directory MySQL will not initialize (unable to attach to server), put it back, MySQL works fine.

Any Input on this one?

Is it possible with LVM to mount sba as /var?

Wombat

---

### Post by koenn on 2010-08-12
I'm not going to write your documentation for you. 
Try the steps I explained, make notes, tweak till it works, keep takin,g noites, and you'll have your documentation.
(Then, using your notes, do it again for real, to see if your procedure is correct :) )
 

hint: look up the -p and -r options to cp (man cp)

tip: You're using vmware, so use yhe snapshot feature


aside: for cloning disks, look up 'dd' and 'clonezilla'


re. disks and partitions ; it makes sense to consider your partitioning needs in terms of directories / disk space you'll need (eg for a separate /web or /database directory, but other than that, this is not relevant to the actual moving of files and directories; unlike on windows, the unix file system hierarch makes abstraction of the underlying volumes.

---

### Post by koenn on 2010-08-12
> **wombat613 said:**
> No go for MySQL

following several web pages, in short
Shut down MySQL
Create new directory give ownership to mysql
copy files over
edit my.cnf
restart MySQL

Anytime I set my.cnf to use the new directory MySQL will not initialize (unable to attach to server), put it back, MySQL works fine.

Any Input on this one?


look in /var/log/syslog for entries that explain why mysql didn't start.

my guess: ownership of the files /subdirs changed when you copied them. 


> 
Is it possible with LVM to mount sba as /var?

yes, of course. 
although LVM has nothing to do with it.

---

### Post by pipemartinm on 2010-08-12
If you're trying to make it repeatable then just do a fresh install and tick the box to manually configure partitions. You can choose what partitions get mounted where really easily. Otherwise just set it in fstab.

---

### Post by wombat613 on 2010-08-16
Update on attempt 3 everything went well.

Created LVM, web and mysql
moved var/www to web/www
moved var/lib/mysql to mysql/mysql

used the cp -r -p to do both

Added users, verified time stamps things looked great

Did Automatic updates

System crashed on "writing new mysql.conf file"

looking at var/log/systemlog

Aug 16 11:51:09 uLamp kernel: [  221.253528] type=1503 audit(1281973869.462:49):  operation="open" pid=2256 parent=1 profile="/usr/sbin/mysqld" requested_mask="rw::" denied_mask="rw::" fsuid=102 ouid=102 name="/mysql/mysql/ibdata1"

looks like an ownership issue has come to roost.

-rw-r--r-- 1 root  root         0 2010-08-16 10:07 debian-5.1.flag
-rw-rw---- 1 mysql mysql 10485760 2010-08-16 11:21 ibdata1
-rw-rw---- 1 mysql mysql  5242880 2010-08-16 11:21 ib_logfile0
-rw-rw---- 1 mysql mysql  5242880 2010-08-16 10:07 ib_logfile1
drwx------ 2 mysql root      4096 2010-08-16 10:10 mysql
-rw-rw---- 1 root  root         6 2010-08-16 10:10 mysql_upgrade_info

[EDIT] From Other Thread :
To fix this, you will need to add /mnt/fastdata/var/lib/mysql (or  whatever non standard path you are using) to the list of authorized  paths in the apparmor mysql profile you will find in /etc/apparmor.d

Done thanks all for help

---

### Post by wombat613 on 2010-08-20
The final Document I put together, may it help someone else find their way.

Wombat

---

