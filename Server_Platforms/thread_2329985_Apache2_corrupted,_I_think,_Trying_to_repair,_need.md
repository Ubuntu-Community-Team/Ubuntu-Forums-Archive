---
title: "Apache2 corrupted, I think, Trying to repair, need assistance."
date: 2016-07-06
forum: Server Platforms
---

### Post by Heeter on 2016-07-06
Hi all,

This is for a working, production Owncloud/Email/Webserver sitting on a LAMP Ubuntu 14.04 



I think that corrupted the apache2 setup. None of the three hosted webpages are pulling up on the browsers. 

I tried this so far:
```

root@server:/home/serv# sudo apt-get install --reinstall apache2 apache2-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of apache2-bin is not possible, since it cannot be downloaded.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 apache2 : Depends: apache2-bin (= 2.4.7-1ubuntu4.10) but 2.4.20-1+deb.sury.org~trusty+3 is to be installed
           Depends: apache2-data (= 2.4.7-1ubuntu4.10) but 2.4.20-1+deb.sury.org~trusty+3 is to be installed
E: Unable to correct problems, you have held broken packages. 
root@server1:/home/serv# sudo dpkg --configure -a
root@server:/home/serv# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@server:/home/serv#

```

And looks like the conf-available & conf-available folders are missing?
```

root@server:/home/serv# ls -a /etc/apache2
.             apache2.conf.dpkg-dist  mods-available  sites-available
..            envvars                 mods-enabled    sites-enabled
apache2.conf  magic                   ports.conf      webdav.password
root@server:/home/serv#

```

What else can I do? Any help would be greatly appreciated as this server has been out of commission for over a week, and the boss is getting frustrated with me. 

Regards

---

### Post by Graham_Willis on 2016-07-07
I think that you should secure your config & data before proceeding further.

1. What did you do immediately before Apache went down?
2. Do you have backup and is it realistic to secure the data if necessary and recover just the OS this way?
3. If the above is not feasible, how about securing the data and reinstalling just the OS (of course you will have to re-introduce configuration)?
4. Is Apache installed on your machine right now and if yes, what happens after you try to start it? Some messages, some logs in error logs?
5. I'd try **apt-get install -f apache2** . BTW, I've never done installing apache2-bin explicitly when installing Apache.
6. Perhaps purging configuration and then reinstalling, **apt-get remove --purge apache2** and then try to install it from scratch.
7. Perhaps removing and purging everything apache-related (from **dpkg -l | grep -i apache** list) and then reinstalling apache.

---

### Post by Heeter on 2016-07-07
Thank you very much, Graham_Willis

In answers to your questions:

1 - I was actually trying to upgrade php, as the version was deprecated that was currently installed. I did manage to upgrade to 5.5.9 (available from the repos)
2 - I can backup all the conf files from the virtual domains and the apache.conf file.
3 - I will try to avoid the reinstall, this a production email server as well, which is currently running on all the desktop thunderbird applications. Making it worse by taking the email down will get me fired...........
4 - Apache is currently installed, and is doing this:
```

root@server:/home/server# service apache2 restart
 * Restarting Apache httpd web server apache2                            [fail]
 * The apache2 configtest failed.
Output of config test was:
env: apache2ctl: No such file or directory

```

5 - this is what I get:
```

root@server1:/home/adminpc# apt-get install -f apache2                          Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 apache2 : Depends: apache2-bin (= 2.4.7-1ubuntu4.10) but 2.4.20-1+deb.sury.org~trusty+3 is to be installed
           Depends: apache2-data (= 2.4.7-1ubuntu4.10) but 2.4.20-1+deb.sury.org~trusty+3 is to be installed
E: Unable to correct problems, you have held broken packages.

```

6, 7 - I am going to try this, wish me luck :(

---

### Post by Graham_Willis on 2016-07-08
By the second point I meant if you have backup of the operating system in the state before it stopped working. If yes, then _**restoring**_ **just the OS** from this backup is an option (should be relatively fast, probably it is possible to do it even without stopping services, just **make sure if there are directories which are better not being restored**, I don't know, but I think /boot can be one of them, it might be valuable to do a test on a virtual machine before you actually do it). On the other hand, as it seems that some apache-related files are simply missing, you can also try to install apache on another machine and copy them from there to the server. Yet another solution is too install Ubuntu on another machine, install web server there properly and mount the partition with data of sites as NFS share. You can also try to compile apache from sources taking care to install it in as isolated directory so that you wouldn't end up with things mixed up even more (./configure --prefix=directory) and then configuring it so that it would point to your sites.

BTW, saying that you cannot take e-mail down, did you mean that it is not an option to stop it even for a while or just that it is not an option to stop it for a longer period of time?

---

### Post by Heeter on 2016-07-10
Hi Graham_Willis

Thank you for sticking with me,

I managed to purge and reinstall apache2

So far apache2 is restarting with no problems, I got most of my webserved applications back online. (Joomla/Owncloud/LDAP/CARDDAV/WEBDAV/CALDAV/WebCalendar)

Now I need a proper way to install roundcube with plugins.

Cannot thank you enough for helping me.

Regards

---

### Post by Graham_Willis on 2016-07-11
Before you install roundcube, make sure that your backups are in order, synchronize them or create new if they aren't, make sure that you're able to restore them in timely manner - of course not using your production machine but a VM or another physical machine. After the troubles you went through I'd definitely check if I'm able to restore backups in timely manner if I were you.

If everything's OK then you can proceed with [https://help.ubuntu.com/community/Roundcube](https://help.ubuntu.com/community/Roundcube) - I was able to successfully install Roundcube on my machine with this tutorial.

---

### Post by Heeter on 2016-07-23
Good Morning Graham_Willis

Just wanted to thank you so much for your assistance, it was greatly appreciated, I am back up and running and my backups are up to date.

I still can't get roundcube and phpmyadmin webGUI's to work, (they are going 404), but I think that it is a settings problem because of my virtual hosts apache setup, I will startup another thread for this.

Regards, and thank you again!

---

