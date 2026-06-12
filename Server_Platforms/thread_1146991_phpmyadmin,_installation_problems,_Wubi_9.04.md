---
title: "phpmyadmin, installation problems, Wubi 9.04"
date: 2009-05-03
forum: Server Platforms
---

### Post by drubdrub on 2009-05-03
Tried to use Synaptic and install phpmyadmin.
[LIST]
[*][http://localhost/phpmyadmin](http://localhost/phpmyadmin) does not work
[*][http://localhost/mysql](http://localhost/mysql) does not work
[*]Other "obvious" attempts do not work
[/LIST]

Examine /var/www and find no trace of phpmyadmin anywhere.  Cruise the Forum (here) and there is a suggestion that the Synaptic installation has problems but an apt-get installation works.  OK, worth a try.
[LIST]
[*]Uninstall phpmyadmin with Synaptic
[*]Install phpmyadmin with apt-get
[/LIST]

Examine /var/www.  There is now a usr/share/phpmyadmin directory with an index.html.  Point the browser at **[http://localhost/usr/share/phpmyadmin](http://localhost/usr/share/phpmyadmin)** and the expected phpmyadmin interface is displayed.  Log in, all seems to work as expected.

I would expect a symlink like /var/www/phpmyadmin to point to /var/www/usr/share/phpmyadmin, so [http://localhost/phpmyadmin](http://localhost/phpmyadmin) would work.  For these reasons, I consider the phpmyadmin installation to be broken.  Or, am I overlooking something?

When I build a symlink /var/www/phpmyadmin/phpmyadmin.html pointing to /var/www/usr/share/phpmyadmin/index.html the following error is displayed.
```

Warning: require_once(./libraries/common.inc.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/usr/share/phpmyadmin/index.php on line 34

Fatal error: require_once() [function.require]: Failed opening required './libraries/common.inc.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/usr/share/phpmyadmin/index.php on line 34
```
The same is true if the link and the target are the equivalent .php files.  This surprises me.

A symlink /var/www/phpmyadmin/phpmyadmin pointing to /var/www/usr/share/phpmyadmin works.  phpmyadmin is displayed, as expected.

Hope this is helpful.  Many thanks!

---

### Post by daboroe on 2009-05-03
> **drubdrub said:**
> Tried to use Synaptic and install phpmyadmin.
[LIST]
[*][http://localhost/phpmyadmin](http://localhost/phpmyadmin) does not work
[*][http://localhost/mysql](http://localhost/mysql) does not work
[*]Other "obvious" attempts do not work
[/LIST]

/mysql does not exist never has. /phpmyadmin should work it is a sym link to another location


> **drubdrub said:**
> 
Examine /var/www and find no trace of phpmyadmin anywhere.  Cruise the Forum (here) and there is a suggestion that the Synaptic installation has problems but an apt-get installation works.  OK, worth a try.
[LIST]
[*]Uninstall phpmyadmin with Synaptic
[*]Install phpmyadmin with apt-get
[/LIST]

Examine /var/www.  There is now a usr/share/phpmyadmin directory with an index.html.  Point the browser at **[http://localhost/usr/share/phpmyadmin](http://localhost/usr/share/phpmyadmin)** and the expected phpmyadmin interface is displayed.  Log in, all seems to work as expected.

I would expect a symlink like /var/www/phpmyadmin to point to /var/www/usr/share/phpmyadmin, so [http://localhost/phpmyadmin](http://localhost/phpmyadmin) would work.  For these reasons, I consider the phpmyadmin installation to be broken.  Or, am I overlooking something?


> **drubdrub said:**
> 
When I build a symlink /var/www/phpmyadmin/phpmyadmin.html pointing to /var/www/usr/share/phpmyadmin/index.html the following error is displayed.
```

Warning: require_once(./libraries/common.inc.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/usr/share/phpmyadmin/index.php on line 34

Fatal error: require_once() [function.require]: Failed opening required './libraries/common.inc.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/usr/share/phpmyadmin/index.php on line 34
```


It is saying that /var/www/usr/share/phpmyadmin/index.php does not exist. I have indicated ways below to try. If those do not work then I would definitely say phpmyadmin is broken. 

> **drubdrub said:**
> 
The same is true if the link and the target are the equivalent .php files.  This surprises me.

A symlink /var/www/phpmyadmin/phpmyadmin pointing to /var/www/usr/share/phpmyadmin works.  phpmyadmin is displayed, as expected.

Hope this is helpful.  Many thanks!

How are you installing it? I would completely remove it and then re install it. You might need to reconfigure the package as well.

```

sudo apt-get remove phpmyadmin
sudo apt-get install phpmyadmin
sudo dpkg-reconfigure phpmyadmin

```

see if that helps youl. i did it the other day through those means and all works fine.

---

### Post by drubdrub on 2009-05-04
Thanks, Daboroe.  Good ideas.  Appreciate your thoughts.

> **daboroe said:**
> /mysql does not exist never has. /phpmyadmin should work it is a sym link to another location

It is saying that /var/www/usr/share/phpmyadmin/index.php does not exist. I have indicated ways below to try. If those do not work then I would definitely say phpmyadmin is broken. 

How are you installing it? I would completely remove it and then re install it. You might need to reconfigure the package as well.

```

sudo apt-get remove phpmyadmin
sudo apt-get install phpmyadmin
sudo dpkg-reconfigure phpmyadmin

```

see if that helps youl. i did it the other day through those means and all works fine.

There actually is an /var/www/usr/share/phpmyadmin/index.html and index.php.
```
lrwxrwxrwx 1 david david   15 2009-05-02 17:32 usr/share/phpmyadmin/index.html -> phpmyadmin.html
-rw-r--r-- 1 david david 6813 2009-01-19 09:35 usr/share/phpmyadmin/index.php
```
That is part of my confusion.  Neither would work when the target of a symlink.  Both caused the error I mentioned in my first post.   Hmmmmmm ...   But, usr/share/phpmyadmin works as a target, so [http://localhost/phpmyadmin](http://localhost/phpmyadmin) works in the browser.  :confused:  So the problem is solved.  phpmyadmin is now functional.

Here are the perceived problems:
[LIST]
[*]Installing with Synaptic failed to produce a functional installation.  There was no sign of phpmyadmin in the /var/www directory structure.  Synaptic was used to remove phpmyadmin.  
[*]"**apt-get install phpmyadmin**" succeeded.  The phpmyadmin configuration utility executed.  The /var/www/usr/share/phpmyadmin directory was created and populated.  There was no link created in /var/www, so [http://localhost/phpmyadmin](http://localhost/phpmyadmin) did not function.
[/LIST]

I'm still thinking a bug report is indicated.  Neither installation method produced a working installation.  That's not so good.

phpmyadmin is a wonderful tool.  Have been using it for a few years.  Installing it via xampp is a snap.  Everything just works.  But, then you don't get the benefits of a package manager tracking package versions and installing updates.

Thanks again.

---

### Post by dipan66 on 2009-05-17
Daboroe - dpkg-reconfigure worked for me. I had installed using apt-get - didnt realize I had mad a mistake in specifying the webserver - removed it, installed it again, reconfigured it - and it worked perfectly. 

Thanks for the good advice.

---

