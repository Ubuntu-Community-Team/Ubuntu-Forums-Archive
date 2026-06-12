---
title: "Apache - install Joomla"
date: 2008-01-13
forum: Server Platforms
---

### Post by expatCM on 2008-01-13
I am trying to install Joomla on my server.  To do so normally you browse to the Joomla files and then follow the install process on screen.  Generally harmless.

The location you are supposed to browse to is the host name or localhost and that brings up the first screen.  In my case I have torrentflux installed on the server and if I browse to the hostname / IP then the torrentflux login appears.

If I browse to [http://hostname/var/www/joomla](http://hostname/var/www/joomla) where the files are located I get a message from Appache saying “The requested URL /var/www/joomla was not found on this server.”.

Does anyone have experience of this ....?


The following thread shows a similar problem
[http://ubuntuforums.org/showthread.php?t=509204](http://ubuntuforums.org/showthread.php?t=509204)
but I am not sure how to translate the solution to my particular case.  The thread suggests adding DocumentRoot "/var/www" to the apache conf which I did but it did not appear to have any effect.

---

### Post by stalker145 on 2008-01-14
> **expatCM said:**
> I am trying to install Joomla on my server.  To do so normally you browse to the Joomla files and then follow the install process on screen.  Generally harmless.

The location you are supposed to browse to is the host name or localhost and that brings up the first screen.  In my case I have torrentflux installed on the server and if I browse to the hostname / IP then the torrentflux login appears.

If I browse to [http://hostname/var/www/joomla](http://hostname/var/www/joomla) where the files are located I get a message from Appache saying “The requested URL /var/www/joomla was not found on this server.”.

Does anyone have experience of this ....?


The following thread shows a similar problem
[http://ubuntuforums.org/showthread.php?t=509204](http://ubuntuforums.org/showthread.php?t=509204)
but I am not sure how to translate the solution to my particular case.  The thread suggests adding DocumentRoot "/var/www" to the apache conf which I did but it did not appear to have any effect.

It sounds like you are running torrentflux listening on port 80. Either change torrentflux to an alternate port or change Apache to listen on something other than 80.

Also, if you were to browse to the Joomla web site, the address would probably be [http://hostname/joomla](http://hostname/joomla) instead of the actual file tree as you have it as Apache, by default, already looks in /var/www.

---

### Post by jmoberly on 2008-01-14
If your files are in var/www you should be able to alternately browse to [http://hostname/installation/install.php](http://hostname/installation/install.php) (or installation.php) (I don't remember).
Normally, you should just be able to go to [http://hostname](http://hostname) and the install will start, but, I have had to go the alternate route once or twice; oddly; on the same server and it was professionally hosted.
Not really sure why though...

---

### Post by expatCM on 2008-01-15
I have tried to change the Apache port from 80 to 90.  Trouble is that even though I applied torrentflux login still appears if I simply enter [http://hostname](http://hostname) in a browser.

I then tried to access 
[http://hostname/installation/install.php](http://hostname/installation/install.php)
and I get an error which says
The requested URL /installation/install.php was not found on this server.
but it does confirm that port 90 is in use.

I varied the path a bit to include joomla and also use the IP rather than the hostname but the same message appears.

---

### Post by expatCM on 2008-01-16
After a few more experiments I have the following situation - 

Torrentflux settings are changed to port 90

If I now go to 
[http://hostname](http://hostname)
I get a directory listing which gives a directory for Joomla, for torrentflux and one for apache.

If I click on the joomla directory the installer now launches which is great :)

Torrentflux is now a problem in that I have to drill down the directory structure to 
[http://hostname/torrentflux/html](http://hostname/torrentflux/html)
before the login page will appear.

There has to be a simple way of putting a short cut in somehow so that I can simply click on the torrentflux directory in order to get this to launch.  Or is this not how things work?

Since I use torrents only about twice a year it is no hardship if this cannot be done ... but if it can ... how?

---

