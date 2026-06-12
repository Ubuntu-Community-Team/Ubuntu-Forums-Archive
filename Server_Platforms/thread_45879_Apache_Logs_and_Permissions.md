---
title: "Apache Logs and Permissions"
date: 2005-07-02
forum: Server Platforms
---

### Post by SychoSly on 2005-07-02
I Ubuntu installed on one of my systems that I am using as a web server. I recently installed log analyzing software so that I can see the stats graphically. 

I pointed the configuration to the apache logs, /var/logs/apache2/access.log , but I am getting permission denied when the software wants to access the log. How do I go about granting apache permissions to read the files?

Thanks.

---

### Post by tigerstripedcat on 2005-07-02
[QUOTE=SychoSly]I Ubuntu installed on one of my systems that I am using as a web server. I recently installed log analyzing software so that I can see the stats graphically. 

I pointed the configuration to the apache logs, /var/logs/apache2/access.log , but I am getting permission denied when the software wants to access the log. How do I go about granting apache permissions to read the files?

Thanks.[/QUOTE]
 If you're talking about awstats, I have the same problem.   The logs will be periodically rotated apache.log will be renamed to apache.log.1 and a new log (for that month?) will be created.  Your options are:

1)  Change permissions/ownership of the file: sudo chown www-data /var/log/apache.log or run chmod
2)  Add www-data to the group adm
3)  Hack the log rotation file to create proper permissions for apache.log

I use the second solution.  It is probably the least secure, but I'm not sure by how much.  I think 3 is the best solution, but I haven't looked into it much.  Someone please correct me if #2 is a large security hole.  Either way, you should probably protect your log directory with an htaccess file.

---

### Post by LordHunter317 on 2005-07-02
If your log directory is web accessible, you're already doing something really dumb.  So it shouldn't ever need a .htaccess file.

As for awstats, I believe the best idea is to have the files owned (user or group) via www-data.  I could be wrong, I don't use it, all I've deployed is webalizer.  You can make rotated logs have the right permissions by editing the proper file in /etc/logrotate.d/.

---

### Post by SychoSly on 2005-07-02
[QUOTE=tigerstripedcat]If you're talking about awstats, I have the same problem.   The logs will be periodically rotated apache.log will be renamed to apache.log.1 and a new log (for that month?) will be created.  Your options are:
[/QUOTE]


I am trying to setup awstats I got it to read the main log file, access.log but then it trys doing something and gets an error saying:

"Error: Couldn't open file "/var/www/awstats/awstats062005.sychosly.tmp.26959" for write: Permission denied 

Setup ('/var/www/awstats/awstats.sychosly.conf' file, web server or permissions) may be wrong.
Check config file, permissions and AWStats documentation (in 'docs' directory). "

Any ideas.

---

### Post by SychoSly on 2005-07-02
[QUOTE=LordHunter317]If your log directory is web accessible, you're already doing something really dumb.  So it shouldn't ever need a .htaccess file.

As for awstats, I believe the best idea is to have the files owned (user or group) via www-data.  I could be wrong, I don't use it, all I've deployed is webalizer.  You can make rotated logs have the right permissions by editing the proper file in /etc/logrotate.d/.[/QUOTE]


My logs are not accessible through the web or if they are I am not aware of it. My web site is as /var/www/ and the logs are at /var/logs/ .

How is webalizer is it somewhat easy to set up?

---

### Post by LordHunter317 on 2005-07-03
The Debian webalizer package just works OOB, at least for me.  It's has to be reconfigured if you host more than one site though.

As for your error, awstats was trying to write the output and failed.  What user does awstats run under?  That user will need write access to the /var/www/awstats directory.

---

### Post by SychoSly on 2005-07-03
[QUOTE=LordHunter317]The Debian webalizer package just works OOB, at least for me.  It's has to be reconfigured if you host more than one site though.

As for your error, awstats was trying to write the output and failed.  What user does awstats run under?  That user will need write access to the /var/www/awstats directory.[/QUOTE]


To tell you the truth I am not sure what user awstats is using. I am guessing it is using the www-data user. How do I check what user it is using?

How do I make www-data(apache user?) part of the admin group?

---

### Post by LordHunter317 on 2005-07-04
[QUOTE=SychoSly]To tell you the truth I am not sure what user awstats is using. I am guessing it is using the www-data user. How do I check what user it is using?[/quote]Look for what user the cron job runs under.  I don't know where it's stored.  If you run:```
sudo crontab -u www-data -l
``` and get the cron job for awstats, that's pretty telling. 

> How do I make www-data(apache user?) part of the admin group?I'm not going to tell you because you really don't want to do this.

---

### Post by SychoSly on 2005-07-04
[QUOTE=LordHunter317]Look for what user the cron job runs under.  I don't know where it's stored.  If you run:```
sudo crontab -u www-data -l
``` and get the cron job for awstats, that's pretty telling. 

I'm not going to tell you because you really don't want to do this.[/QUOTE]


I get "there is no crontab for this user"

SO what does that mean?

---

### Post by GrumpySimon on 2005-07-05
[QUOTE=SychoSly]I get "there is no crontab for this user"

SO what does that mean?[/QUOTE]

Just to back up what LordHunter said - be very careful messing with Awstats if it's accessible via the web. There are a number of automated exploits doing the rounds for it at the moment (generally looking for awstats.pl in /cgi-bin/).

These should, of course, be patched, but better safe than sorry.

--Simon

---

### Post by SychoSly on 2005-07-07
So I am not getting any cron jobs when I search for it the above mentioned way. 

Anyone know why it is getting permission denied errors? What do I have to change?

Thanks.

---

### Post by LordHunter317 on 2005-07-07
You have to give ownership to whatever use awstats runs as.  I don't know what that is, because I don't use it.  You could look in /etc/passwd to see if there is a special account, and check the cron files in /etc

---

### Post by hogman23 on 2006-07-31
Awstats uses www-data to access the logs.  I would guess that you could chown the /var/log/apache2 folder to root:awstats and it would continue to work.  The problem is, when the log file rotates, the permissions change from root:www-data to root:adm.  Because awstats is using www-data to access the log file, it no longer has rights.

---

### Post by snooptodd on 2006-08-24
> **SychoSly said:**
> So I am not getting any cron jobs when I search for it the above mentioned way. 

Anyone know why it is getting permission denied errors? What do I have to change?

Thanks.
Read the file /usr/share/doc/awstats/README.Debian

---

