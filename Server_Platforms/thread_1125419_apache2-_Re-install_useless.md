---
title: "apache2- Re-install useless"
date: 2009-04-14
forum: Server Platforms
---

### Post by Micronot on 2009-04-14
Hi 
Let me start with I'm new to apache & in the beginning stages of learning. Looking at the apache docs, It doesn't look to difficult but I'm finding it difficult with the problems I'm having. Unfortunately I don't remember all the specifics of all that I've tried since I started down this path.
I had it installed and working. I had it configured to go to my test_php page by default (Learning php & MySQL as well). All seemed well except that apache didn't seem to be recognizing the php code (php5 is & was installed)

At some point my key configuration files became empty. I have no idea what happened. I accept that I may have done something stupid causing the disaster. 

Since, I've un-installed & reinstalled the lamp stack. I've also un-installed apache2 on it's own. Most recently-

sudo apt-get remove --purge apache2
sudo apt-get clean
sudo apt-get install apache2

sudo aptitude install apache2-mpm-prefork
sudo dpkg --configure -a
sudo apt-get remove --purge apache2
sudo apt-get clean
sudo apt-get install apache2

_Ya I've been going at it like Elmer Fudd with a shotgun_. No matter what I do-
**All** the directories under /etc/apache2 are empty. 
/etc/apache2/apache2.conf doesn't even exist.
These are persistent problems.

Feed back Please?!?!?!

---

### Post by mbeach on 2009-04-14
can you post the results of:
```
sudo apt-get install apache2
```

---

### Post by Micronot on 2009-04-14
Here is the output-


~$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 45.1kB of archives.
After this operation, 102kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main apache2 2.2.8-1ubuntu0.5 [45.1kB]
Fetched 45.1kB in 0s (57.2kB/s)
Selecting previously deselected package apache2.
(Reading database ... 210438 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.8-1ubuntu0.5_all.deb) ...
Setting up apache2 (2.2.8-1ubuntu0.5) ...
~$ ls -l /etc/apache2


I left the ls -l to show that I had a command prompt after the apt-get process had completed. Also that I checked to see that the problem had not been fixed.
Thanks

---

### Post by cdenley on 2009-04-14
It isn't enough to simply install the php module. You also have to enable it.
```

sudo apt-get install libapache2-mod-php5
sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```

---

### Post by mbeach on 2009-04-14
but does /etc/apache2 remain empty of files or are there some files there now?

what happens when you browse to:
[http://localhost](http://localhost)

anything, or do you get the 'it works' page?  

you should at least have a default file in /etc/apache2/sites-available.

---

### Post by cdenley on 2009-04-14
> **mbeach said:**
> but does /etc/apache2 remain empty of files or are there some files there now?

what happens when you browse to:
[http://localhost](http://localhost)

anything, or do you get the 'it works' page?  

you should at least have a default file in /etc/apache2/sites-available.

Try re-installing the package that contains those files
```

sudo apt-get --reinstall install apache2.2-common libapache2-mod-php5

```

Or probably, since you seem to have deleted files belonging to packages you have installed, maybe you should start with a clean slate
```

sudo apt-get remove ^apache2* ^libapache2*
sudo apt-get install apache2 libapache2-mod-php5
sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```

---

### Post by Micronot on 2009-04-14
**I think** - I did get everything reinstalled. I am happy to say that as far as I know, it looks like all the config files are back. 
The php5 module is enabled. 

When restarting apache I get the following error. 
[B]
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName[/B]

BTW- I also got a similar message upon reinstall.
This is, I'm sure not positive. It doesn't appear to be a fatal error of any sort. I am happy to say that I now get the **"It Works"** page when I go to [http://localhost](http://localhost). 

I would like to fix the FQDM error though as it is disquieting to me.

I'll need to try some php script to make sure everything's functional as far the the php-mod goes.

Do anyone have Ideas or insights that would help me to be sure all my necessary components have been properly reinstalled?

---

### Post by jms1989 on 2009-04-14
It appears you have not specified the nameserver for your apache service. 
Edit /etc/apache2/sites-enabled/000-default and change *:80 to 127.0.0.1:8o, save and restart apache to see if that worked.

---

### Post by cdenley on 2009-04-15
> **jms1989 said:**
> It appears you have not specified the nameserver for your apache service. 
Edit /etc/apache2/sites-enabled/000-default and change *:80 to 127.0.0.1:8o, save and restart apache to see if that worked.

That won't make the warning go away, that will prevent remote connections to your site. You actually need to set the FQDN, as the warning states, to make it go away.

-set ServerName in your site configuration to your FQDN
-edit /etc/hostname to contain your FQDN
-run this command (substituting your actual FQDN)
```

sudo hostname myfqdn.com

```

Make sure you understand what a FQDN is, first.
[http://en.wikipedia.org/wiki/FQDN](http://en.wikipedia.org/wiki/FQDN)

---

### Post by jnat64 on 2009-06-19
I have an extension to ask for help in this forum.  I have installed the packages, get the "It Works" page, 
ran sudo a2enmod php5 --> it reported it enabled, 
have all the php5 items installed, 
what do i need to do to get the browser to receive parsed pages and not a PHP MIME type mismatch : the "Choose a program to open this file type:" dialog box?

I have read and didn't see any glaring misses, and need this for a project to be finished on Sunday 6/21/09.  Any help is greatly appreciated.

I ran even a simple ```
<?php phpinfo(); ?>
```with the same outcome.  If I embed it in HTML, nothing is resolved for the PHP code.

I read some more info at php.net, and it seems you have to include a ```

<FilesMatch "\.ph(p[2-6]?|tml)$">
          SetHandler application/x-httpd-php
</FilesMatch>

``` snippet to httpd.conf to get it completely working.


HTH others.

---

### Post by cdenley on 2009-06-19
> **jnat64 said:**
> 
I ran even a simple ```
<?php phpinfo(); ?>
```with the same outcome.  If I embed it in HTML, nothing is resolved for the PHP code.

By default, apache does not look for PHP code in .html files. You should use scripts with a .php extension.

---

### Post by jnat64 on 2009-06-25
It worked after I included the <FilesMatch> tag, the .html went through OK due to the .ini config, and with the mod_php.

Thanks for the feedback though :)

---

