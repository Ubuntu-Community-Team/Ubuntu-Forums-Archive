---
title: "trouble running php scripts."
date: 2007-04-16
forum: Server Platforms
---

### Post by proxima estacion on 2007-04-16
Running Apache2, MySQL and PHP5. now for some reason when i try and open localhost/test.php instead of bringing up the expected screen, firefox brings up the 'You Have chosen to open/ save' dialog box....if i 'open' the script it just brings up the test.php code not the page...

does this make sense??? any ideas...thanks all

---

### Post by Frosty Cold Drink on 2007-04-16
Is the PHP module enabled? Sounds like Apache doesn't know how to handle it properly, but since I can't see your config files, that's just a wild guess. Check it out to make sure PHP is enabled and the .php file extension is proerply mapped. You should see something like
```
AddType application/x-httpd-php .php
```
somewhere in your config files.

---

### Post by kmoffat on 2007-04-29
I have a similar problem. When I specify the actual file, ([url]/index.php) it loads, but if I just use / ending, not specifying the filename, I get the download dialog. Seems the index.php part of apache2.conf is not working. Also I have some userdirs that work, but some show the download dialog. The DirectoryIndex line seems appropriate:

DirectoryIndex index.html index.htm index.shtml index.cgi index.php index.php3 index.pl index.xhtml index.wml

I think permissions are okay.

---

### Post by G0mez on 2007-04-30
Same here too, I can't see the php5 module anywhere, almost seems like installing libapache2-mod-php5 does nothing, where I presume it should install the files and add the AddType lines.

---

### Post by RichGuk on 2007-04-30
Made sure the mod is enabled?

```
sudo a2enmod php5
```

---

### Post by evanlight on 2007-04-30
> **RichGuk said:**
> Made sure the mod is enabled?

```
sudo a2enmod php5
```

I'm having the same issue. Have tried all the suggestions above and the php5 module is running.  Added php as a filetype in the Apache2 config and re-started. 

It seems that I'm missing some PHP libraries, as my Apache error.log gives me the folllowing. I've re-installed php and have no change.

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/200606$
[Mon Apr 30 16:42:50 2007] [notice] Apache/2.2.3 (Ubuntu) PHP/5.2.1 mod_ssl/2.2$
[Mon Apr 30 17:08:09 2007] [notice] caught SIGTERM, shutting down
[Mon Apr 30 17:08:20 2007] [notice] suEXEC mechanism enabled (wrapper: /usr/lib$
[Mon Apr 30 17:08:20 2007] [error] python_init: Python version mismatch, expect$
[Mon Apr 30 17:08:20 2007] [error] python_init: Python executable found '/usr/b$
[Mon Apr 30 17:08:20 2007] [error] python_init: Python path being used '/usr/li$
[Mon Apr 30 17:08:20 2007] [notice] mod_python: Creating 8 session mutexes base$
[Mon Apr 30 17:08:20 2007] [notice] mod_python: using mutex_directory /tmp
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/200606$
[Mon Apr 30 17:08:21 2007] [notice] Apache/2.2.3 (Ubuntu) mod_python/3.2.10 Pyt$



Any ideas?

---

### Post by kmoffat on 2007-04-30
> **kmoffat said:**
> I have a similar problem. When I specify the actual file, ([url]/index.php) it loads, but if I just use / ending, not specifying the filename, I get the download dialog..

Reply to self. It seems that when I clear out the firefox cache it functions properly. This is some strange new behavior. Further, I removed all index* files except the one I want (index.html~, index.html.bak, index.php.bak, etc.) Not sure if this matters.

---

### Post by RichGuk on 2007-05-01
> **evanlight said:**
> I'm having the same issue. Have tried all the suggestions above and the php5 module is running.  Added php as a filetype in the Apache2 config and re-started. 

It seems that I'm missing some PHP libraries, as my Apache error.log gives me the folllowing. I've re-installed php and have no change.

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/200606$
[Mon Apr 30 16:42:50 2007] [notice] Apache/2.2.3 (Ubuntu) PHP/5.2.1 mod_ssl/2.2$
[Mon Apr 30 17:08:09 2007] [notice] caught SIGTERM, shutting down
[Mon Apr 30 17:08:20 2007] [notice] suEXEC mechanism enabled (wrapper: /usr/lib$
[Mon Apr 30 17:08:20 2007] [error] python_init: Python version mismatch, expect$
[Mon Apr 30 17:08:20 2007] [error] python_init: Python executable found '/usr/b$
[Mon Apr 30 17:08:20 2007] [error] python_init: Python path being used '/usr/li$
[Mon Apr 30 17:08:20 2007] [notice] mod_python: Creating 8 session mutexes base$
[Mon Apr 30 17:08:20 2007] [notice] mod_python: using mutex_directory /tmp
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/200606$
[Mon Apr 30 17:08:21 2007] [notice] Apache/2.2.3 (Ubuntu) mod_python/3.2.10 Pyt$



Any ideas?

I'm not too sure, the only thing I have in /usr/lib/php5 that has 200606 in it is a folder called;

/usr/lib/php5/20060613+lfs and in that I have 

mysqli.so  mysql.so  pdo_mysql.so  pdo.so  snmp.so


Which PHP5 package do you have installed. I wasn't to sure as I compile PHP5 myself but I have just setup a virtual machine with ubuntu on and I appear to have libapache2-mod-php5 installed, but there is also a package called php5.

Maybe try --purge?

```
sudo apt-get remove --purge php5 libapache2-mod-php5
```

And then installing again

```
sudo apt-get install libapache2-mod-php5
```

If not, maybe give PHP4 a go, see if that works?




> **kmoffat said:**
> Reply to self. It seems that when I clear out the firefox cache it functions properly. This is some strange new behavior. Further, I removed all index* files except the one I want (index.html~, index.html.bak, index.php.bak, etc.) Not sure if this matters.

Could be Firefox, I've had times when certain URL's just don't want to load I spent ages trying to work it out and it turns out just restarting firefox fixes it :p.

---

### Post by proxima estacion on 2007-05-07
Thanks all, not quite sure which thread i used to fix it, but its all good now...cheers :guitar:

---

### Post by evanlight on 2007-05-08
> **RichGuk said:**
> I'm not too sure, the only thing I have in /usr/lib/php5 that has 200606 in it is a folder called;

/usr/lib/php5/20060613+lfs and in that I have 

mysqli.so  mysql.so  pdo_mysql.so  pdo.so  snmp.so


Which PHP5 package do you have installed. I wasn't to sure as I compile PHP5 myself but I have just setup a virtual machine with ubuntu on and I appear to have libapache2-mod-php5 installed, but there is also a package called php5.

Maybe try --purge?

```
sudo apt-get remove --purge php5 libapache2-mod-php5
```

And then installing again

```
sudo apt-get install libapache2-mod-php5
```




**BINGO!**  Works perfectly now - thanks!

---

### Post by Siamang on 2007-05-09
I had tried multiple things to no avail and was getting frustrated when I finally cleared my Firefox cache. Worked fine after that, thanks for the suggestion.

---

### Post by proxima estacion on 2007-05-13
> **evanlight said:**
> **BINGO!**  Works perfectly now - thanks!


Whoooah, yeah thanks, that did the trick...thank you ...

---

### Post by kmoffat on 2007-05-13
I guess the question I have is why this has never been necessary in the past?

---

