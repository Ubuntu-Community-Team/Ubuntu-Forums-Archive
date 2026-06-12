---
title: "Installing Bugzilla"
date: 2009-10-13
forum: Server Platforms
---

### Post by tkhobbes on 2009-10-13
Hi all, trying desperately to install Bugzilla. The bugzilla package installs kind of odd - it places stuff into /usr/share/bugzilla3, and when I symlink it to /var/www, I somehow can access bugzilla, but only without styles... I found various articles on the net, but they were referring apparently to older versions of the package.... in sum, I could not install bugzilla properly. What EXACTLY do I need to do once the package is installed?

---

### Post by Queue29 on 2009-10-14
> **tkhobbes said:**
> Hi all, trying desperately to install Bugzilla. The bugzilla package installs kind of odd - it places stuff into /usr/share/bugzilla3, and when I symlink it to /var/www, I somehow can access bugzilla, but only without styles... I found various articles on the net, but they were referring apparently to older versions of the package.... in sum, I could not install bugzilla properly. What EXACTLY do I need to do once the package is installed?

Looks like I posted the exact same question before google could pick up your post...

[http://ubuntuforums.org/showthread.php?t=1291391](http://ubuntuforums.org/showthread.php?t=1291391)

---

### Post by tkhobbes on 2009-10-17
Read through your post, and it's really odd - it seems that the apache-conf files are not even installed on my box. I reinstalled bugzilla3 various times (i. e. removed it and installed it again, but it did not help.
Somehow, the package seems really, really broken - but launchpad did not yield any results relating to this... but then maybe we should wait until octover 29th for karmic?

---

### Post by tkhobbes on 2009-10-23
*bump*

Anyone?

---

### Post by Versusnja on 2009-10-23
Well, i installed bugzilla3
sudo apt-get install bugzilla3

answered questions during the installation.
Then went to /etc/apache/conf.d, copied contents of symlinked bugzilla config and created a virtual host in apache2/sites_available" and symlinked to apach2/sites_enabled (for uniformity).

First start of virtual host - everything works with all styles.

Hope this helps.

---

### Post by tkhobbes on 2009-10-25
apt-get bugzilla3 installs a hell lot of packages, asks me for the 
database administrator password and then whether I changed values for "Status/Resolution" - when I answer "yes", the installation aborts, when I answer "no", it continues.
The tables are added (can confirm this via phpmyadmin), 
BtW, it installs bugzilla 3.2.0.1.1.

It runs through and then says something about changing the system parameters (most notably the URI or "urlbase") - which has to be done in the webfrontend of bugzilla.

HOWEVER - there is NOTHING created in neither /etc/apache2/conf.d nor in /etc/apache2/sites-available. I think this is the problem here.....

---

### Post by Versusnja on 2009-10-25
I found an EXCELLENT solution to bugzilla3 problem. See here [www.thebuggenie.com](www.thebuggenie.com)
It's not perfect and has some problems. But it still works GREAT.

"Hell lot of packages" in 90% refer to installing perl. There's nothing really special.
Bugzilla is a perl based web page with mysql support. So, after installing and checking that you have the tables you should simply tell apache where to look for the bugzilla.
Unfortunatelly, I deleted bugzilla3 after I found the Bug Genie, but if I were you, I would manually create bugzilla config in sites-enabled and restarted apache with
sudo /etc/init.d/apache2 restart

---

### Post by tkhobbes on 2009-10-26
I would create the config-file - but how do I find out what is supposed to be in there?

In the meantime - I will look at the Bug Genie :)

---

### Post by Versusnja on 2009-10-26
I decided to install the bugzilla3 again to send you the confir file for Apache, but for some reasons it didn't create any apache configs this time.

I could try to write the config myself, but try the bug genie first and let me know.

Technically, you should create a virtual host in apache with the root folder in /usr/share/bugzilla3
and a few aliases. I remeber one for sure, which is cgi-bin, pointing at /usr/lib/cgi-bin/bugzilla3

For what reason didn't they install everything at /var/www/bugzilla3 and why the installation doesn't create apache config - I have NO idea.

---

### Post by tkhobbes on 2009-10-27
I installed buggenie and I am fine with this. However, the problem is not solved, which is why I will not mark the thread accordingly.

---

### Post by Bunzinator on 2009-10-28
> **tkhobbes said:**
> Hi all, trying desperately to install Bugzilla. The bugzilla package installs kind of odd - it places stuff into /usr/share/bugzilla3, and when I symlink it to /var/www, I somehow can access bugzilla, but only without styles... I found various articles on the net, but they were referring apparently to older versions of the package.... in sum, I could not install bugzilla properly. What EXACTLY do I need to do once the package is installed?

Is your symlink as below?...

```
ln -s /usr/share/bugzilla3/web /var/www/bugzilla3
```

I had the same issue... using this symlink fixed it for me.

I

---

### Post by Versusnja on 2009-10-28
There's not use with the symlink since there is no apache config file at all.
So, symlink won't help.

---

