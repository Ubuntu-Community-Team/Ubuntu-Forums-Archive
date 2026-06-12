---
title: "Can't set up MySQL"
date: 2006-08-09
forum: Server Platforms
---

### Post by ryharv on 2006-08-09
Hello all,

I'm trying to set up MySQL with no luck.  I've browsed around the forums and found other users with similar problems to those I'm having, but I tried their solutions and they're not working for me.

i'm having trouble taking the initial step of changing the mysql root password, but before i can even get there i need to get the server up and running.  here is what happens:

sudo /etc/init.d/mysql start
df: `/var/lib/mysql/.': No such file or directory
/etc/init.d/mysql[19729]: ERROR: The partition with /var/lib/mysql is too full!

any suggestions?

---

### Post by mlind on 2006-08-09
Is your root partition too full? Mysql seems to fail on creating the initial database.

To see how much space you've got available
```

df -h

```

---

### Post by ryharv on 2006-08-10
Thanks for replying...

None of my partitions are actually full.  When I run df I get:

```
ryan@rybuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3              3028108   2333892    540396  82% /
varrun                  128120       152    127968   1% /var/run
varlock                 128120         4    128116   1% /var/lock
udev                    128120       100    128020   1% /dev
devshm                  128120         0    128120   0% /dev/shm
lrm                     128120     18856    109264  15% /lib/modules/2.6.15-26-386/volatile
/dev/hda1              3020140     93408   2773316   4% /boot
/dev/hda4            185143856  53515592 122223412  31% /home

```

Here is what I get when I try to do anything with mysql:

```
ryan@rybuntu:~$ sudo /etc/init.d/mysql start
df: `/var/lib/mysql/.': No such file or directory
/etc/init.d/mysql[5514]: ERROR: The partition with /var/lib/mysql is too full!
```

I've removed and reinstalled mysql-server many times using 

sudo apt-get remove mysql-server

and then

sudo apt-get install mysql-server

After each time I reinstall it, I try to set up the root password using the following command, and I get the following response:

```
ryan@rybuntu:~$ mysqladmin -u root password mypassword
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

Then I run sudo /etc/init.d/mysql start and get the problem above.

Any ideas?

---

### Post by rich on 2006-08-11
Is this a partition problem ?

I've never got too involved in the dark art of slicing disk space, but is it possible that your two /var partitions are too specific ?

Without a /var where is /var/lib supposed to go ? I'd stick a gig or two into /var and see what happens. 


Then again, I could be completely on the wrong track. 



Rich

---

### Post by lamego on 2006-08-11
```
/var/lib/mysql/
```
Do you have such directory ?
If you do not then your mysql installation is seriously broken. This directory is used to store the database itself.

---

### Post by az on 2006-08-11
Why do you have such a partition scheme?  How are they mounted?  What permissions and ownership do they have?

Offhand, I don't know under what user mysqld runs, but it probably doesn't have access to those directories because of how they are set up in fstab?

And you shouldn't have to manually start and stop mysql.  It start when installed and upon boot.  Youwould have to stop it manually to need to restart it manually.

---

### Post by kalariwarrior on 2007-12-04
/etc/init.d/mysql start
df: `/var/lib/mysql/.': No such file or directory
/etc/init.d/mysql[19729]: ERROR: The partition with /var/lib/mysql is too full!

Got this after my /var directory was trounced. You don't need to know the details except that it was ugly.

For restoring /var (which apt and dpkg need stuff from to run...), I had great success with making empty dirs as needed for apt and by copying various /var/lib folders from another Ubuntu comp on the network for dpkg and such. It might have been easier to just reinstall but I was too lazy to find my cds.

---

### Post by koenn on 2007-12-04
> **rich said:**
> Is this a partition problem ?

I've never got too involved in the dark art of slicing disk space, but is it possible that your two /var partitions are too specific ?

Without a /var where is /var/lib supposed to go ? I'd stick a gig or two into /var and see what happens. 


Then again, I could be completely on the wrong track. 



Rich
/var us just a subdirectory of / so unless the admin assigns a particular partition to it, /var will be on the same partition as /

---

### Post by koenn on 2007-12-04
do
 
```
ls -l /var
ls -l /var/lib
ls -l /var/lib/mysql
```
to find out what part of the path is missing, and to see the owners and permissions 

then, take it from there. 
It's possible something went wrong during the consiguration of mysql-server.

---

