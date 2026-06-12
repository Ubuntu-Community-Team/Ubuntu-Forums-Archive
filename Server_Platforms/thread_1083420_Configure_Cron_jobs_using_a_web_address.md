---
title: "Configure Cron jobs using a web address"
date: 2009-02-28
forum: Server Platforms
---

### Post by R.Bucky on 2009-02-28
I host my domain using Ubuntu Server 8.04 with Webmin for... Well, you know. My CMS, Concrete5, has the option of clearing the cache via a web address. I would like to automate this using Webmin. I have no idea how to do this. Possibly a cron job? Or, is there a better method, aside from creating a bookmark and clicking on it?

---

### Post by Thirtysixway on 2009-03-01
You can setup cron jobs inside of webmin.  You can use one of these commands:

lynx -source [http://example.com/cron.php](http://example.com/cron.php)
wget -O - -q -t 1 [http://example.com/cron.php](http://example.com/cron.php)
curl --silent --compressed [http://example.com/cron.php](http://example.com/cron.php)

---

### Post by JeppeM on 2009-03-01
The question is wheter or not the page is password protected, and if it is, in what way...

Could you try going to the page when another browser (opera for example), just to see if you have to enter a password to get into it (using another browser makes sure that there's no things just as sessions or saved cookies which interfer with the test). If you have to enter your password, then please report back with which way you have to enter if (if it's on the page itself, or in an HTTP Auth box).

Oh, and just to add to Thirtysixway's list, you can also use wget --spider [http://example.com/cron.php](http://example.com/cron.php) :)

---

