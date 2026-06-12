---
title: "testing php after installing apache2"
date: 2007-04-04
forum: Server Platforms
---

### Post by Mia_tech on 2007-04-04
after installing apache2 and php4, I have created a test page called "testphp" at the server root so I would access the page as in [http://localhost/testphp.php](http://localhost/testphp.php), the test page contain the following code

<?php phpinfo(); ?>

which is expected to give me in webpage with all the php info, but instead I get prompted to download the page and the it opens as a .txt fie and I'm looking at the code  instead of the webpage

any ideas as to why that is happening

thanks

---

### Post by rjfioravanti on 2007-04-04
Did you add the line necessary in httpd.conf to parse php files?

---

### Post by Mia_tech on 2007-04-04
> **rjfioravanti said:**
> Did you add the line necessary in httpd.conf to parse php files?

what lines?......this is a laptop and I have a desktop with exactly the same isntallation and it works................anyways what lines are those?

---

### Post by rjfioravanti on 2007-04-04
Look at step 6 on this page

[http://fioravengi.homelinux.com/tutorials/apache-php/](http://fioravengi.homelinux.com/tutorials/apache-php/)

let me know how it goes

---

### Post by Mia_tech on 2007-04-04
well my httpd.conf file is not there my installation using the repos is in /etc/apache2/httpd.conf.....I added those lines and tried to restart apache with no luck.....got error, something about not able to load modules....here it is.

 * Forcing reload of apache 2.0 web server...                                   Syntax error on line 6 of /etc/apache2/httpd.conf:
LoadModule takes two arguments, a module name and the name of a shared object file to load it from
                                                                         [fail]

---

### Post by rjfioravanti on 2007-04-04
Make sure you have the package

libapache2-mod-php5

installed. Then check /etc/apache2/apache2.conf to see that it has the line

DirectoryIndex ..... and the list includes index.php

---

### Post by Mia_tech on 2007-04-04
> **rjfioravanti said:**
> Make sure you have the package

libapache2-mod-php5

installed. Then check /etc/apache2/apache2.conf to see that it has the line

DirectoryIndex ..... and the list includes index.php

yep, it's there and the mod-php5 file is installed

---

### Post by rjfioravanti on 2007-04-04
and is the DirectoryIndex line in your conf file with index.php included on the line?

are you restarting like this

sudo /etc/init.d/apache2 restart

?


If so, how are you accessing you page, and are you still being asked to download the php file by your browser?

---

### Post by lishevita on 2007-04-09
I am having this EXACT SAME PROBLEM. Here's what I've done so far, to no avail:

[LIST]
[*] Attempted to dpkg-reconfigure each of the packages connected with PHP or Apache2
[*] Found out that php5.conf and php5.load were not in the /etc/apache2/mods-enabled directory and so ln -s 'd them from the mods-available directory.
[*] Banged head against desk
[*] restarted apache using sudo /etc/init.d/apache2 restart instead of the usual   sudo /usr/sbin/apache2ctl -k graceful  just for good measure...
[/LIST]

But, nope. Still no joy. Any more ideas, folks?

---

### Post by lishevita on 2007-04-09
Oh, by the way, here's the last line of my error log:

[Mon Apr 09 16:03:28 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 mod_perl/2.0.2 Perl/v5.8.
8 configured -- resuming normal operations


And there are no other errors that make it look like there *should* be a problem. So, PHP5 is there, but it's not working. Whyyyyyyy???

---

### Post by rjfioravanti on 2007-04-09
the packages from the repos work out of the box for me

All i can recommend is that you try uninstalling everything completely, not sure what the package names are exactly but I would do something like

sudo apt-get autoremove php5 apache2 php5-common apache2-common libapache2-mod-php5 etc etc, get all names!

then search your system for any files left over, then reinstall wtih the following command

sudo apt-get install php5 apache2 libapache2-mod-php5

---

