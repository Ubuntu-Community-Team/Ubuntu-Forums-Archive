---
title: "Apache2 php parsing problem"
date: 2006-08-15
forum: Server Platforms
---

### Post by Randy_84dger on 2006-08-15
Hello!

<preamble>
I'm trying to get apache2, php5 mysql set up on my 6.06 desktop for general web-dev/messing around. Previously (5.10) everything went smoothly from apt, taking the relevant packages, then dumping stuff in /var/www (phpMp2, drupal webmin etc). Having performed a clean (nuked / and reinstalled) upgrade to 6.06 things aren't behaving.:sad: 
</preamble>

Apache is serving htm, html etc fine, but  php files dont parse.

I followed the community docs here ([https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)), php5 module is enabled, but firefox still wants to save me a lovely phtml file [-o<

I've searched the forums, but nothing has fixed it. Have read about XAMPP, but would rather keep things as apt would have it, for later troubleshooting (assuming php starts behaving)

I suspect its a simple config file tweak, but can't understand why apt-getting the packages on 6.06 hasn't produced a working setup.

Cheers,
Al.

---

### Post by az on 2006-08-15
> **Randy_84dger said:**
> Hello!

<preamble>
I'm trying to get apache2, php5 mysql set up on my 6.06 desktop for general web-dev/messing around. Previously (5.10) everything went smoothly from apt, taking the relevant packages, then dumping stuff in /var/www (phpMp2, drupal webmin etc). Having performed a clean (nuked / and reinstalled) upgrade to 6.06 things aren't behaving.:sad: 
</preamble>

Apache is serving htm, html etc fine, but  php files dont parse.

I followed the community docs here ([https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)), php5 module is enabled, but firefox still wants to save me a lovely phtml file [-o<

Apache or apache2?

A common pitfall is to have both installed and then  mistake libapache-mod-php5 for libapache2-mod-php5... or the same for php4...

---

### Post by Randy_84dger on 2006-08-15
> Apache or apache2?

A common pitfall is to have both installed and then mistake libapache-mod-php5 for libapache2-mod-php5... or the same for php4...
Synaptic was reporting all modules with the correct apache**2** and php**5** package flavours. 

Decided to reinstall the damned thing, complete removal of all packages. Followed the community docs again:
> sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server
Got the phtml offers again.
Followed the troubleshooting:
> sudo apt-get install libapache2-mod-php5
Reading package lists... Done
Building dependency tree... Done
libapache2-mod-php5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Fine, its already there. Then
> sudo a2enmod php5
This module does not exist!


Now I'm confused. (tho it might help troubleshoot the problem?)

Al.

---

### Post by lvanderree on 2006-08-15
When you go to:
```
cd /etc/apache2/sites-available
```
and type
```
ls
```

do you then see the two files:
php5.conf
php5.load

Because these files are supposed to come along with libapache2-mod-php5
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=php5.conf&searchmode=searchfiles&case=insensitive&version=dapper&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=php5.conf&searchmode=searchfiles&case=insensitive&version=dapper&arch=i386)

If not try to reinstall libapache2-mod-php5
```

sudo apt-get remove libapache2-mod-php5
sudo apt-get install libapache2-mod-php5

```
*Ps. if someone knows a better way of reinstalling packages, please tell me... And I don't mean dpkg-reconfigure*

If the do exist, then I'm confused why 
```
sudo a2enmod php5
```
doesn't work, but you can try to make the links manually:
```

sudo ln -s /etc/apache2/mods-available/php5.load /etc/apache2/mods-enabled/php5.load 
sudo ln -s /etc/apache2/mods-available/php5.conf /etc/apache2/mods-enabled/php5.conf 

```

---

### Post by az on 2006-08-15
> **Randy_84dger said:**
> 

Now I'm confused. 

Me too!

exacly what apache and php packages do you have installed?

dpkg -l |grep php
dpkg -l |grep apache

---

### Post by Kurt` on 2006-08-15
> **lvanderree said:**
> When you go to:
```
cd /etc/apache2/sites-available
```
and type
```
ls
```

do you then see the two files:
php5.conf
php5.load


I think you mean /etc/apache2/mods-available :)

---

### Post by Randy_84dger on 2006-08-16
Thanks for the replies. It is now fixed, but I'm no clearer as to why :twisted: 

Following a late night of beer and cursing, a rough summary of the results:

Kurt, ls /etc/apache2/mods-available ... no php5.conf or load (despite being a fresh install). 
azz, looked at the dpkg -l results couldn't see anything "wrong" so decided to nuke all results and every package with apache, php or mysql in the name (possibly not the best plan, but hey). Re-installed as per docs. Didn't work. More beer. Completely removed everything again. Swore lots. Left it un-installed and shut down (both the computer and myself). 
Woke up. Followed the docs, loaded http://localhost/test/index.php and it worked... :shock: 

To summarize, EH?!

I'm more confused than ever. Despite the increase in typos, perhaps drunken web administration would be a wise career move!

Cheers!
Al

---

### Post by lkagan on 2006-08-19
The problem ..... caching.  You fixed the issue, probably many times.  Just like I did right now.  It took me a minute to figure out that since the Zend engine isn't parsing the script there are no headers being sent about expiration or cache.  Thus each subsequent response you got was coming from your cache.  I just ran a packet sniffer and verified this.  Also, since you got that download offer, there's no 'refreshing' the page in the browser since it was never really a page.  All it took was clearing the cache or disabling the cache if you use the firefox web developer toolbar.

Larry

---

### Post by Randy_84dger on 2006-08-19
Good point, well made. Didn't really think about it, possibly should have. Thanks for the info, will bear it in mind. :D 

Al.

---

### Post by chrisfay on 2006-08-19
> Re-installed as per docs. Didn't work. More beer. Completely removed everything again. Swore lots. Left it un-installed and shut down (both the computer and myself). 
Woke up. Followed the docs, loaded [http://localhost/test/index.php](http://localhost/test/index.php) and it worked...  

Anyone else laughing at this

---

### Post by aleska on 2006-08-22
> **lkagan said:**
> The problem ..... caching.  You fixed the issue, probably many times.  Just like I did right now.  It took me a minute to figure out that since the Zend engine isn't parsing the script there are no headers being sent about expiration or cache.  Thus each subsequent response you got was coming from your cache.  I just ran a packet sniffer and verified this.  Also, since you got that download offer, there's no 'refreshing' the page in the browser since it was never really a page.  All it took was clearing the cache or disabling the cache if you use the firefox web developer toolbar.

Larry
Larry Kagan you are my hero!  I've uninstalled and reinstalled all this LAMP crap again and again.  Same problems over and over and over.  Wow!  I'm amazed that the answer could be so simple.  Thanks man!
BTW - if you don't have the firefox web developer tool bar, you can clear by going to Edit -> Preferences -> Cache Tab -> Clear Cache Now button.
Thanks again!

---

### Post by aleska on 2006-08-22
> **Randy_84dger said:**
> 
Woke up. Followed the docs, loaded [http://localhost/test/index.php](http://localhost/test/index.php) and it worked... :shock: 
Al

What you didn't tell us was that just before going to bed you surfed enough porn on the net to replace the 50MB of cache your browser was storing, thereby clearing the way for your local php to actaully be served!  :p 

...so, in truth, it is both the drunken web administration AND porn that helps!  ;)

---

### Post by lkagan on 2006-08-22
Careful there!  If my ego gets any more inflated, I'd be an MCSE!

Larry Kagan

---

### Post by Randy_84dger on 2006-08-22
Objection, your honour!

(Tho who'd have thought porn could possibly help on so many levels)

---

### Post by goneskiing on 2006-08-22
More beer helps - Seriously, I have had same wacky frustrating problem.  I think it is as above mentioned, a problem with caching.  In short, after you know all the right modules and settings are there, close server down.  Reboot.  Start server again.  Maybe even twice.  Then it all works.  btw I've had same issue with reading php permissions.  Again rebooting helped.  Somehow caching doesn't get cleared out with simple server restart.

---

### Post by Almighty on 2006-08-22
I am having the same problem with parsing. Last night I set up a small web forum. Everything was working fine when I quite for the night. I didnt not shut the server down or anything. Got up this morning to see I have this parsing problem. Even after reading this thread I am still lost to what I should do.

---

### Post by lkagan on 2006-08-22
You say you are having the same problem. You mean instead of parsing the page, it's asking you to download it? Did you clear your browser cache?  Do you have the following line in your site-specific apache config file (/etc/apache2/sites-enabled/<site_name>)?
```
AddType application/x-httpd-php .html
```
Did you restart apache?  Did you check your apache error log (/var/log/apache/error.log)?  If you did all this, give me some more details and we'll figure out what the problem is.

Larry Kagan

---

### Post by Almighty on 2006-08-22
> **lkagan said:**
> You say you are having the same problem. You mean instead of parsing the page, it's asking you to download it? Did you clear your browser cache?  Do you have the following line in your site-specific apache config file (/etc/apache2/sites-enabled/<site_name>)?
```
AddType application/x-httpd-php .html
```
Did you restart apache?  Did you check your apache error log (/var/log/apache/error.log)?  If you did all this, give me some more details and we'll figure out what the problem is.

Larry Kagan

I have the same issue with the browser wanting to download the php file instead of parsing the page.

I have cleared the browser cache
The php modules are for Apache2
php5.conf and php5.load are listed in sites-available
 Also when I try a forced retart of Apache2 it fails because the httpd is not running. The error log shows nothing that is out of the ordinary.

Under /etc/apache2/sites-enabled there is a file labled 000-default and nothing else.

Im about ready to uninstall everything and try it from the beginning myself.

---

### Post by Almighty on 2006-08-22
Nevermind everyone this thread helped me fix it. I dont know how since I did everything they said. I guess it is the order in which you do it that makes the difference.

[http://www.ubuntuforums.org/showthread.php?t=147063&highlight=apache2+php+woes]("http://www.ubuntuforums.org/showthread.php?t=147063&highlight=apache2+php+woes")

---

### Post by hebetude on 2007-11-18
I actually had this problem, probably due to the fact that I had previously removed php5.  Anyways...

Go into synaptic do a complete removal on libapache2-mod-php5 (or whatever you have installed) then install it.  This will tell it to actually install the config files, which weren't there but it was not installing for some reason.

Synaptic saves the day again

---

