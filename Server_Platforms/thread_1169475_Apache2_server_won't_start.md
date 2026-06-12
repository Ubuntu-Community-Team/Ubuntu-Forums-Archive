---
title: "Apache2 server won't start"
date: 2009-05-25
forum: Server Platforms
---

### Post by b00mer on 2009-05-25
When I try to start Apache webserver from webmin, I get the following error:

Failed to start apache :

 * Starting web server apache2
apache2: Syntax error on line 281 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/500-squirrelmail: No such file or directory
   ...fail!

When I go to /etc/apache2/sites-enabled/500-squrrelmail,the file icon has an "X" over it and says "(link broken) 


I've uninstalled both Apache SquirrelMail and reinstalled them thinking that would work, and it didn't  I've uninstalled just squirrelMail and tried to start the webserver and that didn't work.

I'm running Ubuntu Desktop 9.04, Apache2, Postfix Mail server 2.5.5, SquirrelMail 1.4.15

Any help would be appreciated.

Thanks

---

### Post by masmad on 2009-05-25
The problem most likely is that the squirrelmail site is still enabled as apache sees it. 

If you don't need squirrelmail, you can use the command
```
sudo a2dissite 500-squirrelmail
```
to disable that site.

If you need it, you should reinstall squirrelmail and try to start apache again. After that post possible errors..

---

### Post by b00mer on 2009-05-25
I removed SquirrelMail, re-installed it, rebooted the machine, and still got the same error when trying to start Apache.  

I did the sudo a2dissite 500-squirrelmail command, and the webserver started.  I would remove squirrelmail, but I think I need it for pop3 access to the mail... or at least have a webmail interface.  If Anyone has a different approach, I would love to hear it.

Thanks

---

### Post by afbase on 2009-05-25
I would recommend [swift mailer](http://swiftmailer.org/)

---

### Post by koenn on 2009-05-25
> **b00mer said:**
> 
apache2: Syntax error on line 281 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/500-squirrelmail: No such file or directory
   ...fail!

When I go to /etc/apache2/sites-enabled/500-squrrelmail,the file icon has an "X" over it and says "(link broken) 



 /etc/apache2/sites-enabled/500-squirrelmail should be a symbolic link to a file in /etc/apache2/sites-available, probably /etc/apache2/sites-available/500-squirrelmail. It's possibly the file in sites-available that's missing, hence the "broken link". Or the link is pointing to the wrong location.
The quick fix then would be to ```
rm /etc/apache2/sites-available/500-squirrelmail
``` and create a new one (with ln -s or a2ensite)


If /etc/apache2/sites-available/500-squirrelmail is actually missing, you should 
- figure out why that file disappeared (or why it wasn't there to begin with), and/or
- create a suitable /etc/apache2/sites-available/500-squirrelmail, containing a valid apache conf for squirrel web mail (or extract on from a .deb)

---

