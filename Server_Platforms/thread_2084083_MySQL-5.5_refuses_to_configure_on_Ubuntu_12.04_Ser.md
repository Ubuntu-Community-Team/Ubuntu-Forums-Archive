---
title: "MySQL-5.5 refuses to configure on Ubuntu 12.04 Server"
date: 2012-11-14
forum: Server Platforms
---

### Post by archonic_one on 2012-11-14
I did the obligatory searching, I believe this is posted in the right place / not previously solved.

This problem is described on [SuperUser here]("http://superuser.com/questions/502822/cant-start-mysql5-5-on-ubuntu-12-04-dpkg-dependency-problems"). I'll reiterate here.

**I've tried:**

```

sudo apt-get clean

sudo apt-get autoclean

sudo apt-get remove --purge mysql-client-5.5 mysql-client-core-5.5 mysql-common mysql-server mysql-server-5.5 mysql-server-core-5.5

sudo apt-get install mysql-server

```

I'm getting the same results as before which are as follows:

```

apt-get install -f mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
mysql-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up mysql-server-5.5 (5.5.24-0ubuntu0.12.04.1) ...
120907 21:37:15 [Note] Plugin 'FEDERATED' is disabled.
120907 21:37:15 InnoDB: The InnoDB memory heap is disabled
120907 21:37:15 InnoDB: Mutexes and rw_locks use GCC atomic builtins
120907 21:37:15 InnoDB: Compressed tables use zlib 1.2.3.4
120907 21:37:15 InnoDB: Initializing buffer pool, size = 128.0M
120907 21:37:15 InnoDB: Completed initialization of buffer pool
120907 21:37:15 InnoDB: highest supported file format is Barracuda.
120907 21:37:15  InnoDB: Waiting for the background threads to start
120907 21:37:16 InnoDB: 1.1.8 started; log sequence number 154164236
120907 21:37:16  InnoDB: Starting shutdown...
120907 21:37:16  InnoDB: Shutdown completed; log sequence number 154164236
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.

Errors were encountered while processing:
 mysql-server-5.5
 mysql-server

```


**In addition:**
```

dpkg-reconfigure mysql-server-5.5
/usr/sbin/dpkg-reconfigure: mysql-server-5.5 is broken or not fully installed

```

Anyone else in my boat? I've been searching for a few days and tried everything reasonable I've found. Really don't want to re-install -_-

---

### Post by andrewcaveman on 2012-11-19
Greetings, 

I had the same issue. Tried the apt-get clean, autoclean, remove and apt-get install mysql-server-5.5

Same error would keep coming up. 

I removed everything a second time, tried again, still the same problem. 

This is what worked for me, though I was doing an install and not an upgrade, so I didn't care about the existing database. 

I removed all the mysql application again, then I went and deleted my /var/lib/mysql directory. 
Keep in mind, if you have an existing database there, you will lose it. You might want to move it to another location. 

After removing that directory, I installed again and it worked perfect. So something in the /var/lib/mysql directory was my problem. See if that works for you. 

Best, 
-andrewcaveman

---

### Post by chmurson on 2012-11-19
Thanks andrewcaveman!

I was was trying various of solution but after an hour or so, yours finally did a job! Thank you!

---

### Post by MikeG0 on 2012-12-07
> **andrewcaveman said:**
> Greetings, 

I had the same issue. Tried the apt-get clean, autoclean, remove and apt-get install mysql-server-5.5

Same error would keep coming up. 

I removed everything a second time, tried again, still the same problem. 

This is what worked for me, though I was doing an install and not an upgrade, so I didn't care about the existing database. 

I removed all the mysql application again, then I went and deleted my /var/lib/mysql directory. 
Keep in mind, if you have an existing database there, you will lose it. You might want to move it to another location. 

After removing that directory, I installed again and it worked perfect. So something in the /var/lib/mysql directory was my problem. See if that works for you. 

Best, 
-andrewcaveman

this worked for me too.  thanks!

---

### Post by fireballmatt on 2012-12-12
I had the same issue as was originally reported in this thread (actually came from the first thread on it that was marked as SOLVED)

I didn't want to go through the process of restoring the databases if I couldn't help it, so I deleted everything in the /var/lib/mysql directory that WASN'T a database. 

I then repeating the clean/autoclean process outlined in the original post of this thread worked for me.

---

### Post by Suncat2000 on 2013-03-16
@andrewcaveman: Thanks! I repeated the clean process several times without success. I didn't know what files in /var/lib/mysql were relevant and which were not, so I just renamed the directory (in case I needed to rebuild my databases later), purged, and reinstalled. Afterward, mysql 5.5 installed and started without complaint. Thanks to everyone for their suggestions.

---

### Post by defaultstring on 2013-04-26
> **andrewcaveman said:**
> Greetings, 

I had the same issue. Tried the apt-get clean, autoclean, remove and apt-get install mysql-server-5.5

Same error would keep coming up. 

I removed everything a second time, tried again, still the same problem. 

This is what worked for me, though I was doing an install and not an upgrade, so I didn't care about the existing database. 

I removed all the mysql application again, then I went and deleted my /var/lib/mysql directory. 
Keep in mind, if you have an existing database there, you will lose it. You might want to move it to another location. 

After removing that directory, I installed again and it worked perfect. So something in the /var/lib/mysql directory was my problem. See if that works for you. 

Best, 
-andrewcaveman

Thanks!  Your solution also worked for my paticular installation of 12.04 as well.

I would, however, like to know more about why this worked, though.  What motivated you to remove the entirety of /var/lib/mysql?  I think it might be valuable to explore the explicit details of why this fix works.

---

### Post by azath on 2013-08-20
I had the same issue, and found it could be easily reproduced on 12.04 by:
apt-get remove mysql-server
apt-get install mysql-server

Even when I removed /var/lib/mysql and /etc/mysql, dpkg would fail to update the password again. 

At this point, mysql would fail to start, and a "apt-get remove --purge mysql-server" would trigger dpkg to configure mysql-server again, which would also fail. Same for mysql-server-5.5. 

What finally worked for me was 
dpkg --purge mysql-server-5.5

Then I was able to fully purge everything else. Note that when I ran apt-get autoclean, it seemed to wipe something, so that when I ran apt-get autoremove --purge, it didn't recall the original mysql-server dependancies. But when I ran apt-get remove --purge mysql-common it included some other deps, and then running apt-get autoremove --purge found some other things. 

After all that, I was able to apt-get install mysql-server again, and everything worked, including setting the password. 

Hope this helps someone!

---

