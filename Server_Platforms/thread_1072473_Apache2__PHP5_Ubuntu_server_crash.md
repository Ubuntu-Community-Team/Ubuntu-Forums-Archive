---
title: "Apache2 / PHP5 Ubuntu server crash"
date: 2009-02-17
forum: Server Platforms
---

### Post by aasimpson on 2009-02-17
Hello. I would greatly appreciate any helpful feedback on this issue.

On 2 occasions last week, we became aware that our vitally important business web server was not working properly. On both occasions I quickly found that the cause was PHP 5, which we run as the standard Apache module for apache-mpm-prefork, libapache2-mod-php5, having completely frozen up without any obvious explanation. Apache 2 itself was found to be working perfectly, as plain HTML files and images were served as normal, as were Perl CGI scripts. But PHP was completely out of action. I managed to (temporarily at least) resolve the problem, on the first occasion by uninstalling and reinstalling libapache2-mod-php5 using apt-get, and on the second occasion by using dpkg-reconfigure on the same package and restarting Apache.

Nonetheless, we seek an explanation, so that we might be properly armed against any further repeat. We are greatly alarmed that having fixed this issue one evening, and thinking it to be a freak one-off occurrence, it happened again the following morning with exactly the same symptoms. We worry that perhaps we are being maliciously attacked in some way. On the other hand, this could be a crash due to an unlikely software bug?

The crash floods our Apache system error logs with literally millions of whitespace-separated zeros e.g. 0 0 0 0 0 0 0 0 --:--:-- 0:05:05 --:--:-- 00 0 0 0 0 0 0 0 --:--:-- 0:05:05.

Ubuntu: Hardy Heron version packages.

That's about as much information as I can gather. Thank you in advance for any help. All ideas welcome.

-- Andrew.

---

### Post by bettlebrox on 2009-02-17
This isn't enough info to go on, yet! :( Change Apache's logging level from the default warn to debug to see if it provides more info.

In /etc/apache2/apache2.conf change:
LogLevel warn
To:
LogLevel debug

Restart Apache and see if there's anything in:
/var/log/apache2/access.log
/var/log/apache2/error.log

---

### Post by tubezninja on 2009-02-17
Additionaly, since it looks unlikely that a software reinstall will fix this, uninstalling and reinstalling probably isn't the best way to get apache2/php going again.  Just telling the service to restart is more efficient:

```
sudo /etc/init.d/apache2 restart
```


Lastly, can you paste some of these lines with 0 0 0's in their entirety, in addition to any new info that the debug LogLevel gives you?  It would be helpful to know if these lines are actual GETs from an outside source, or if something else is going on.

---

### Post by aasimpson on 2009-02-18
> **scaredpoet said:**
> Additionaly, since it looks unlikely that a software reinstall will fix this, uninstalling and reinstalling probably isn't the best way to get apache2/php going again.  Just telling the service to restart is more efficient:

```
sudo /etc/init.d/apache2 restart
```


Lastly, can you paste some of these lines with 0 0 0's in their entirety, in addition to any new info that the debug LogLevel gives you?  It would be helpful to know if these lines are actual GETs from an outside source, or if something else is going on.
Hi. Thanks, but restarting the service as you described was naturally the very first thing I tried, but it made no difference as the crash was so severe, and so more drastic action like reinstalling/reconfiguring the libapache2-mod-php5 package was needed, and did fix the problem.

Perhaps I should reiterate in case I wasn't clear about this: I fixed the server already, however I have no idea of HOW IT CAME TO CRASH. That is what we need to know: how did this most likely happen -- through malicious intent or a software bug or something -- so that we might be better prepared against it in the future.

Any suggestions/theories are always much appreciated.

---

### Post by aasimpson on 2009-02-18
> **bettlebrox said:**
> This isn't enough info to go on, yet! :( Change Apache's logging level from the default warn to debug to see if it provides more info.

In /etc/apache2/apache2.conf change:
LogLevel warn
To:
LogLevel debug

Restart Apache and see if there's anything in:
/var/log/apache2/access.log
/var/log/apache2/error.log
Thanks for this suggestion, I'll try that and see if it digs up any further clues/info.

---

