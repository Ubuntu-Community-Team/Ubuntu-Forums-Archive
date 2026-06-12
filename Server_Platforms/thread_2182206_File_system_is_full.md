---
title: "File system is full"
date: 2013-10-20
forum: Server Platforms
---

### Post by yesjohn on 2013-10-20
Hello everybody, 

I am running Ubuntu 12:04 lts on a web server. We migrated our server a few weeks ago because we needed some more space. The migration went fine but yesterday Ubuntu gave a prompt that our file system was almost full. I cleaned a few things and it worked fine again. This morning we had the same error and we can't log in to the desktop interface anymore (low graphics mode). 

This is what i get when I use the du command:
 [IMG]http://img22.imageshack.us/img22/4521/ucfu.png[/IMG]

When I use sudo apt-get clean it works for a few seconds but when I login in the normal interface it sends me back to the low graphics mode. I already searched on Google but i couldn't find a solution that worked for me. Hopefully you can help me out :)

---

### Post by Bashing-om on 2013-10-20
yesjohn; Hi ! Welcome to the forum.

Do this to get an idea as to what is going on.
```

df -h
df -i
du -h --max-depth=1 | sort -hr
cd /
sudo du -h --max-depth=1 | sort -hr
cd ##gets you back to your /home directory as the present working directory.
ls -la /boot

```
Suspecting that log files are running away, /boot partition is full, or too many apps installed. These commands will indicate where all the disk space is being used, and also the number of inodes available.

[INDENT][INDENT]good as any place to start
[/INDENT][/INDENT]

---

### Post by yesjohn on 2013-10-20
Thanks for your reply !!


df -h :

[IMG]http://img802.imageshack.us/img802/5422/zdrm.png[/IMG]

df -i:

[IMG]http://img703.imageshack.us/img703/633/hab0.png[/IMG]
du -h --max-depth=1 | sort -hr

[IMG]http://img842.imageshack.us/img842/2492/xjba.png[/IMG]
ls -la /boot

[IMG]http://img69.imageshack.us/img69/6527/ww4t.png[/IMG]

The sudo du -h --max-depth=1 | sort -hr command only gave me a flashing line. :confused:

---

### Post by Bashing-om on 2013-10-20
yesjohn; Not good !

Quite frankly I am out of my depth with this: "/dev/mapper/EM ->XXX".
1. Are we dealing with an encrypted partition ? I have never been there. Logical volume management ?
2, How in the world are you booting the server, as there are no kernels present in the /boot partition ? - /dev/vda1 is what ?
3. We now know that it is the "/" [root] that is full, but we can not see it (as the "du" command just flashes).
4.  I do not see the directory "/var" listed, in your server you do not have "/var" as a separate partition ? -- maybe if "/var" is under "/" the logs are running away ? and we can delete some of those old logs to get us some head space and see what we can then see ?


Off topic; code tags: please use them as it does make your output more readable, as is I can not copy/paste your output. see:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
for the code tag tutorial.


More questions than answers but ->
[INDENT][INDENT][INDENT]yry'n to get an understanding
[/INDENT][/INDENT][/INDENT]

---

### Post by yesjohn on 2013-10-20
1. I believe I selected lvm during the installation
2. I use Windows most of the time but if i'm remembering it correctly Ubuntu ask where you want to select a folder and i believe boot is one of the options. I always choose / there (if that's what you mean)  
3. I will try it again because I think its the only thing I can do at the moment. 
4. I don't have a separate var partition, I will try to delete some logs

I will use code tags the next time ;)

---

### Post by Bashing-om on 2013-10-20
yesjohn;

I am concerned as to how you are booting, and if you were to shut this server down would it even boot ? .. it always amazes me what I do not know, but with no kernels installed in the "/boot" directory, I do not know how you are able to boot. That is one area of concern.
for your reference; here is my listing of "/var/log"
```

sysop@1304mini:~$ ls -la /var/log
total 3608
drwxr-xr-x  9 root   root   4096 Oct 20 11:03 .
drwxr-xr-x 12 root   root   4096 Oct 19 22:31 ..
-rw-r--r--  1 root   root    682 Oct 15 17:41 alternatives.log
-rw-r--r--  1 root   root    832 Sep 23 21:49 alternatives.log.1
-rw-r--r--  1 root   root    305 Aug 28 23:35 alternatives.log.2.gz
-rw-r--r--  1 root   root    134 Aug  2 12:17 alternatives.log.3.gz
-rw-r--r--  1 root   root   2850 Jul  4 00:08 alternatives.log.4.gz
drwxr-xr-x  2 root   root   4096 Oct  1 09:17 apt
-rw-r-----  1 syslog adm    1250 Oct 20 15:17 auth.log
-rw-r-----  1 syslog adm   36759 Oct 20 10:58 auth.log.1
-rw-r-----  1 syslog adm    2355 Oct 13 12:20 auth.log.2.gz
-rw-r-----  1 syslog adm    3390 Oct  6 12:03 auth.log.3.gz
-rw-r-----  1 syslog adm    3387 Sep 29 09:50 auth.log.4.gz
-rw-r-----  1 root   adm      31 May 19 10:54 boot
-rw-r--r--  1 root   root   1098 Oct 20 10:58 boot.log
-rw-rw----  1 root   utmp      0 Oct  1 09:17 btmp
-rw-rw----  1 root   utmp    768 Sep 23 16:45 btmp.1
drwxr-xr-x  2 root   root   4096 Oct  1 09:17 ConsoleKit
drwxr-xr-x  2 root   root   4096 Apr 19  2013 dist-upgrade
-rw-r-----  1 root   adm   56093 Oct 20 10:58 dmesg
-rw-r-----  1 root   adm   56227 Oct 19 10:11 dmesg.0
-rw-r-----  1 root   adm   14649 Oct 18 12:17 dmesg.1.gz
-rw-r-----  1 root   adm   14699 Oct 17 11:28 dmesg.2.gz
-rw-r-----  1 root   adm   14640 Oct 16 13:39 dmesg.3.gz
-rw-r-----  1 root   adm   14687 Oct 15 19:21 dmesg.4.gz
-rw-r--r--  1 root   root  41886 Oct 15 20:05 dpkg.log
-rw-r--r--  1 root   root  51444 Sep 27 22:24 dpkg.log.1
-rw-r--r--  1 root   root   2826 Aug 29 23:32 dpkg.log.2.gz
-rw-r--r--  1 root   root    610 Aug  2 12:17 dpkg.log.3.gz
-rw-r--r--  1 root   root  48574 Jul 30 00:24 dpkg.log.4.gz
-rw-r--r--  1 root   root  32032 May 19 11:24 faillog
-rw-r--r--  1 root   root    965 May 19 11:23 fontconfig.log
drwxr-xr-x  2 root   root   4096 May 19 10:54 fsck
drwxr-xr-x  3 root   root   4096 May 19 11:04 installer
-rw-r-----  1 syslog adm       0 Oct 20 11:03 kern.log
-rw-r-----  1 syslog adm  755240 Oct 20 10:58 kern.log.1
-rw-r-----  1 syslog adm  199328 Oct 13 12:20 kern.log.2.gz
-rw-r-----  1 syslog adm  230273 Oct  6 12:03 kern.log.3.gz
-rw-r-----  1 syslog adm  262620 Sep 29 09:50 kern.log.4.gz
<snip>

```
The terminal command:
```

ls -la /var/log

``` in a standard install will list the files present.
In this situation, where the info in the logs may prove of immense value, only delete the old compressed files as for example //-rw-r-----  1 syslog adm  262620 Sep 29 09:50 kern.log.4.gz, -rw-r-----  1 root   adm   14687 Oct 15 19:21 dmesg.4.gz, -rw-r-----  1 syslog adm   16820 Oct 14 11:20 syslog.7.gz //
Note the numeric.gz - the oldest files should be safe to delete.

Another concern is that you are short on inodes for the file system. Lots and lots of small files ? .. you might consider repartitioning - as this is a server - and putting "/var" into it's own partition. That would preclude ever filling the "/" partition up from run-a-way logging.
for reference; mine:
```

sysop@1304mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       4.7G  1.5G  3.0G  34% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           2.0G   36K  2.0G   1% /tmp
tmpfs           396M  380K  396M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  516K  2.0G   1% /run/shm
none            100M     0  100M   0% /run/user
/dev/sda2       9.5G  1.1G  8.0G  13% /home
/dev/sda8       4.7G  330M  4.2G   8% /var
sysop@1304mini:~$

```
Once we have a bit of head room we can look closer at the "/var/" directory:
```

du -h --max-depth=1 /var

``` to see what is taking up the space.

[INDENT][INDENT]we be try'n
[/INDENT][/INDENT]

---

### Post by hawkmage on 2013-10-20
The command "sudo du -h --max-depth=1 / | sort -hr" is the one that would give us an idea of what top level directory that is consuming the space.  Since your / volume has over 3 millions inodes you have a large number of files/directories  so it will take a while to run.

---

