---
title: "backup ubuntu server"
date: 2011-05-29
forum: Server Platforms
---

### Post by uuser1221 on 2011-05-29
Hi,
I an new to Ubuntu, we have one Ubuntu server for that we need to configure backup.

Please help me in configuring the backup of the server in the best possible approach.
Also share the Disaster recovery process of Ubuntu Server.

Server details:
# uname –a Linux redmine 2.6.32-27-server #49-Ubuntu SMP Thu Dec 2 02:05:21 UTC 2010 x86_64 GNU/Linux

Any help will be highly appreciated.

Thanks.

---

### Post by HermanAB on 2011-05-29
$ man rsync

It is a one liner.  Examples are in the man page.

If it is not a one liner, then you are doing it wrong.

---

### Post by Lars Noodén on 2011-05-29
> **HermanAB said:**
> $ man rsync

It is a one liner.  Examples are in the man page.

If it is not a one liner, then you are doing it wrong.

+1 for rsync.  It is the way to go for backup.  A more complicated way would be to use Bacula.

---

### Post by LightningCrash on 2011-05-29
What do you want to backup **to**?
Internet, USB disk, Tape drive, another computer somewhere, etc.


Do you just need backups for DR purposes, or is there a possibility that you will frequently need to retrieve old files?


How long do you want to keep your backup files?


There's no one great solution for everyone.

---

### Post by uuser1221 on 2011-05-30
Hi,

Many thanks for your valuable replies.

Actually we have an Enterprise backup solution, HP Data protector, but it does not support Ubuntu.
So I am exploring the best possible backup procedure to be implemented for this Ubuntu server.
The backup is mainly for DR purpose, with daily backup frequency and 1 week retention policy.

We would like to backup it in the existing HP Enterprise Tape library but I am afraid if it supports Ubuntu server.

Or  we would like to backup the Ubuntu server to a Redhat Linux server which is being backed-up daily to the Tape Library using HP Data Protector.

So, please let me know how can I backup this Ubuntu server to the Redhat Linux server.

Thanks again.

---

### Post by drdos2006 on 2011-05-30
Here is how I back up my webserver

I installed nfs-kernel-server and nfs-common on the server to be able to mount the server directory on my desktop backup machine.
I edited the server /etc/exports file to allow sharing on the server /var/www directory.
The MySQL database is automatically updated every day.
The bash commands are run from the desktop terminal to mount the server shares on my desktop.
From the terminal I run:

sudo bash /home/me/Documents/MountWebServer.sh
sudo bash /home/me/Documents/BackupWebServer.sh

//////////////////////////////////////////////////
My MountWebServer.sh file is :
# !/bin/bash

# if statd is not running...
sudo service statd start

#			Server				Client
sudo		mkdir /media/web-var-www
sudo		mount 192.168.0.150:/var/www 	/media/web-var-www
////////////////////////////////////////////////////
My BackupWebServer.sh file is :

# !/bin/bash

rsync  --verbose --recursive  --archive --modify-window=1 --times --update  --delete    --progress --itemize-changes --log-file=/home/c2d-geoff/Documents/backup-log-webserver.txt  /media/web-var-www/*    	/media/sda2/webpages
/////////////////////////////////////////////////////
regards

---

### Post by uuser1221 on 2011-06-08
Hi,

I configured the backup as;

rsync -a -v -q --progress --stats / --exclude /proc root@backup_server:/backup >>/tmp/rsync.log 2>>/tmp/rsync.log


Earlier the whole filesystem was included in the backup even "/proc" filesystem, but one strange behaviour was observed,
On the source server the complete filesystem size is around 6 GB but the backup size was more than 28 GB and growing, when I checked the filesystem size the "/proc" filesystem contains data more than 22 GB but the source server's "/proc" size was 0.

Can anyone figure out why this happened?


I will set cronjob with the above rsync command.

Please let me know if any changes needed to made on the backup procedure?

Thanks.

---

### Post by Lars Noodén on 2011-06-08
In addition to skipping /proc you'll probably also want to skip /sys and /dev

---

### Post by uuser1221 on 2011-06-08
hi,

Ok, we will skip /dev adn /sys as well

rsync -a -v -q --progress --stats / --exclude /proc --exclude /sys --exclude /dev root@backup_server:/backup >>/tmp/rsync.log 2>>/tmp/rsync.log

Will update you after finishing the backup.

Thanks!

---

### Post by Lars Noodén on 2011-06-08
Later when you have it running the way you like it, you can drop the remote root login by [customizing sudo](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup#Backup_with_rsync_and_sudo).  You can do that by adding a new user and then giving that user exactly what is needed in sudoers to run rsync, nothing more.

---

### Post by uuser1221 on 2011-06-08
Hi,
Thanks for your reply.
I have configured the SSH without password by copying the RSA key to the backup_server, the rsync is running without asking for password.

I completed the backup while skipping /dev, /sys and /proc it completed successfully but the size on the backup server which is "RedHat Linux" server is slightly bigger than the Source server.

rsync -a -v  --progress --stats / --exclude /proc --exclude /sys --exclude /dev root@backup_server:/backup >>/tmp/rsync.log 2>>/tmp/rsync.log

_**Source Server**_
root@Source_server:/# **du -ks**
du: cannot access `./proc/29439/task/29439/fd/4': No such file or directory
du: cannot access `./proc/29439/task/29439/fdinfo/4': No such file or directory
du: cannot access `./proc/29439/fd/4': No such file or directory
du: cannot access `./proc/29439/fdinfo/4': No such file or directory
**[COLOR="Red"]6481818[/COLOR]** .
root@Source_serve:/# ls
bin    etc             lib         mnt   sbin     tmp      vmlinuz.old
boot   home            lib64       opt   selinux  usr
cdrom  initrd.img      lost+found  proc  srv      var
dev    initrd.img.old  media       root  sys      vmlinuz

_**Backup_Server**_
[root@Backup_server Backup]# du -ks
[COLOR="red"]**6585732**[/COLOR] .
[root@Backup_server Backup]# ls
bin    dev   initrd.img      lib64       mnt   sbin     sys  var
boot   etc   initrd.img.old  lost+found  opt   selinux  tmp  vmlinuz
cdrom  home  lib             media       root  srv      usr  vmlinuz.old

Can you tell me why there is difference in sizes?

Thanks!

---

### Post by Lars Noodén on 2011-06-08
> **uuser1221 said:**
> 
I have configured the SSH without password by copying the RSA key to the backup_server, the rsync is running without asking for password.

Make sure to lock down [/etc/sudoers](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup#Backup_with_rsync_and_sudo) or else the key itself so that it can **only** run rsync for the backup.

---

