---
title: "HTTP Error 500 - Joomla Install"
date: 2017-07-11
forum: Server Platforms
---

### Post by Daniel_Clarke on 2017-07-11
Hey All,

I am currently using Ubuntu 16.04 and have been for awhile with APACHE as a VPS server. We have multiple websites working properly, however yesterday I went through the same process I have 6-7 times before while setting up a new virtual host for a joomla install and after completing the exact same steps that have worked before I am now getting a HTTP ERROR 500. I am new to all of this and have been able to get myself this far, however this is throwing me for a loop and I can't seem to figure out where I went wrong, if anyone is willing to help resolve this issue or has suggestions it would be very appreciated.

In the event I missed giving information that may be needed to troubleshoot please ask and I would be glad to provide.

Thanks

-daniel

---

### Post by QIII on 2017-07-11
Hello!

Have you tried looking in the Apache error log?

Are you using a Joomla template?  This could indicate something wrong in the php, which might not be logged and hard to catch.

---

### Post by Daniel_Clarke on 2017-07-11
Hi,

Just looked here:

sudo nano /var/log/apache2/error.log

and found this:

**PHP Fatal error: Cannot use Joomla\\String\\String as String because 'String' is a special class name in /var/www/nasbtest.com/public_html/libraries/vendor/joomla/registry/src/Format/Json.php on line 12**

I am not sure what this ALL means other than PHP is having an issue, my concern is this is the same install package I used in the recent past and seems to be working fine. However for good measure I will re-download and try again. 

Any additional suggestions or help would be appreciated in the  event this does NOT fix it.

Thanks

-daniel

---

### Post by Daniel_Clarke on 2017-07-11
It appears the old installer package for the Joomla Theme I had downloaded several months ago was not compatible with PHP 7. I downloaded the latest version and it appears it is working now. I am assuming it was the version of Joomla that was in the installer.

Thanks

daniel

---

### Post by Habitual on 2017-07-11
500 errors are server-side only errors.
```
cat /var/log/apache2/error.log 
```
should enlighten you.
```
sudo tail -f /var/log/apache2/error.log 
``` will "watch" the file using tail in follow mode, or tail -f
Ctrl +c kills the tail.

500 errors are generally, in my experience, due to a mis-configured AllowOverride directive file that can cause 500s.

Without any editing, you can test this claim by simply renaming /var/www/site/.htaccess and testing the site again for 500s.
or set 
```
AllowOverride All
``` in the  
```
**<Directory /var/www/html/>**
``` stanza of /etc/apache2/sites-enabled/000-default.conf

Well, pre-post I see an update wrt PHP7, so any hoos, I'm gonna leave this nugget here for another miner. :)

Have a Great Day!

---

