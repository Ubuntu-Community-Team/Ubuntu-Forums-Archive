---
title: "Php.ini location"
date: 2009-05-17
forum: Server Platforms
---

### Post by wattaman on 2009-05-17
I'm trying to use a different php.ini for every website I have on my server but it seems every site loads the same php.ini.
So, I've added this in one of my *etc/apache2/sites-available/site1.conf*: **PHPINIDir /home/site1**, and it works. I can see this on the phpinfo page:
- Configuration File (php.ini) Path: */etc/php5/apache2*
- Loaded Configuration File: */home/site1/php.ini*

The problem is that the phpinfo for all the other sites is the same; all of them are using the php.ini file located in the */home/site1* folder.
Also, I've tried to add the **PHPINIDir /home/site2** in the site2 conf file, *etc/apache2/sites-available/site2.conf*, but when I try to apply the changes to apache I got this: 
> Syntax error on line 20 of /etc/apache2/sites-enabled/site2.conf:
Only first PHPINIDir directive honored per configuration tree - subsequent ones ignored

So, long story short: **How can I use different php.ini files for different servers**?
Thank you!

---

