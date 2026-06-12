---
title: "mysql tmpdir"
date: 2011-03-14
forum: Server Platforms
---

### Post by geppetto1 on 2011-03-14
I am trying to change the tmpdir from /tmp to /tmp2 which is a new, mounted filesystem.  I am running Ubuntu 10.10 +updates, 10.04 is also available.
I have matched the permissions, ownership, group, and sticky bit:

drwxrwxrwt  13 root root  4096 2011-03-14 00:35 tmp
drwxrwxrwt   2 root root  4096 2011-03-09 02:40 tmp2

and made the necessary changes to 

/etc/mysql/my.cnf: (there are no other (.)my.cnf's on the systems) 
 
tmpdir        = /tmp2 
 
specified /tmp2 in /etc/init/mysql.conf:  (called by /etc/init.d/mysql start) 
 
exec /usr/sbin/mysqld --tmpdir=/tmp2 
 
and stopped and restarted MqSQL (I use Webmin) 
 
But when ever I attempt to execute something I get an error.  This is from an attempt to view user permissions via Webmin: 
 
SQL desc `user` failed : Can't create/write to file '/tmp2/#sql_41ad_0.MYI' (Errcode: 13) 
 
I don't see an apparmor process running  (ps -ef).  I understand it could prevent me from trying to do this.
 
Can anyone tell me what I missed?

Thank you.

---

### Post by wongo888 on 2011-03-15
Check your apparmor settings

```
$ sudo apparmor_status
```

Check messages for audit events:

```
$ cat /var/log/messages
```

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

---

### Post by SeijiSensei on 2011-03-15
Why not just mount tne new filesystem at /tmp?

---

### Post by geppetto1 on 2011-03-15
@ wongo888 - Thank you.  That was it!  I wasn't familiar with apparmor and thought it wasn't running since I didn't see a process running.  

After shutting down MySQL and apparmor, I added '/tmp2/*  rw,' to /etc/apparmor.d/usr.sbin.mysqld and modified /etc/mysql/my.cnf to redirect tmpdir to /tmp2.  Once I restarted apparmor and MySQL, I was able to execute a user permissions query from Webmin.

I did attempt to modify /etc/apparmor.d/local/usr.sbin.mysql to enable a local override but was unsuccessful.


@ SeijiSensei - The thought had occurred to me...  even mounting it as /tmp/tmp2 or something similar.  I was trying to find the Ubuntu equivalent to a UNIX SVR4 Run Level 1  (yep, old knowledge can be dangerous) in order to make the change when I saw the replies.   Another thought was to shutdown and fire up a Puppy Linux Live CD to mount the filesystems and make the necessary changes to mount as /tmp.  It was frustrating trying to figure out why I couldn't just make the changes and have it work.  

Thank you for your replies!

---

### Post by SeijiSensei on 2011-03-15
Suppose the new filesystem is in the /dev/sdb1 partition and formatted with ext4 ("sudo mkfs -t ext4 /dev/sdb1").  You'll need to edit /etc/fstab as root with sudo ("sudo nano /etc/fstab") and add this line to bottom of the file
```

/dev/sdb1   /tmp    ext4     defaults  0 0

```

That will mount /dev/sdb1 at /tmp on reboot.  

(You can usually mount an entry in /etc/fstab at the command line immediately with "sudo mount /mount/point", e.g., "sudo mount /tmp", but I wouldn't do that while logged in.  It's likely that the desktop environment software like KDE or GNOME has written files to /tmp.  Taking those files "out from under" the desktop environment while logged in isn't a good thing to do. Better to reboot and have all the mount points sort themselves out.)  

Before you reboot, copy anything in /tmp that seems worth saving to your home directory, then delete them from /tmp.

---

