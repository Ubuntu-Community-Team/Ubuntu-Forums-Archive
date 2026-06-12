---
title: "PHP or python as cgi won't work on apache2"
date: 2008-02-26
forum: Server Platforms
---

### Post by oliwynn on 2008-02-26
Hi,

I recently reinstalled ubuntu because I made a huge error in my system (thats a whole other story but its fixed now).  I installed apache2, php and mod_python but I can't get php or python to run on my webserver.  the httpd.conf is blank which i think is strange and everytime i try to reinstall all of them the same thing happens, they don't work!  Its getting frustrating trying to solve this problem as I seem to be just going round in circles.

Ive tried many different solutions, ones from the forums here, from ubuntu guides wikis and even got some of my friends from my computing degree course to fix it and they cant!! 

What the hell is wrong with it!!??

Index of /
[ICO]	Name	Last modified	Size	Description
[DIR]	apache2-default/	20-Nov-2004 20:16 	-
[ ]	testphp.php	27-Feb-2008 00:10 	20
Apache/2.2.4 (Ubuntu) Server at localhost Port 80

testphp.php just decides it wants to save

i need some help

thanks in advance 

O

---

### Post by faulkes on 2008-02-26
httpd.conf by default is blank in the ubuntu apache2 installation, do not concern yourself
about that.  The configuration has been moved to /etc/apache2/apache2.conf as well
as the sites-available & sites-enabled directories.

When you install apache2 and php modules, you *must* restart the httpd server process
for php to be recognized.

```

/etc/init.d/apache2 restart

```

This is a known bug in the current apach2 package and is being actively worked on
by the Server Team.

If you still have issues after trying the above, please feel free to continue with this
thread and we will help you as best we are able.

Faulkes

---

### Post by oliwynn on 2008-02-26
Thanks for the quick response,

Still no luck I'm afraid, Ive restarted the server several times and still cannot get it to recognize php5.  Ive been through all the installation guides all similar to this:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Apache_and_PHP5]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Apache_and_PHP5")

and the server still wont recognize php5 or python

any ideas?

O

---

### Post by faulkes on 2008-02-26
Check /etc/apache2/mods-enabled and ensure that php5.load and php5.conf exist there (they should be symlinks).  Then check the contents:

```

michael@fs1:~$ cat /etc/apache2/mods-enabled/php5.load
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so

```

```

michael@fs1:~$ cat /etc/apache2/mods-enabled/php5.conf
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

```

and finally, check /var/log/apache2/error_log for any error messages.

Faulkes

---

### Post by oliwynn on 2008-02-27
Thanks for that it did the trick. 

When I did cat on those files it said file does not exist even though php5 and all its libraries are installed.  I created them and now php5 works fine with ubuntu.  

Now for python as cgi or mod_python.  Does anyone know how to get this to work on apache2?  I need it for my degree course as python is are main programming language.  

Thanks again

O

---

### Post by faulkes on 2008-02-27
> **oliwynn said:**
> 
Now for python as cgi or mod_python.

First, check that it is installed

```

aptitude show libapache-mod-python

Package: libapache-mod-python
**State: not installed**
Version: 2:2.7.11-2
Priority: optional

```

Note that this is from my system, your system may have it installed already, so check that
bold text first after you issue the command.

If it isn't installed:

```

sudo apt-get install libapache-mod-python

```

Then check /etc/apache2/mods-available and /etc/apache2/mods-enabled to
make sure it is 1. available and 2. enabled.

If it is not in the mods-enabled directory (symlinks, probably python.conf, 
python.load), then use the command (I believe the below is correct).

```

sudo a2enmod python

```

You will then likely need to restart apache again for it to pickup the new
module configuration.

Faulkes

---

### Post by oliwynn on 2008-02-27
Thanks for the fast response,

Ive tried what you said

> aptitude show libapache-mod-python

and

> sudo apt-get install libapache-mod-python

this is what i get back:

> oliver@oliver-desktop:~$ aptitude show libapache-mod-python
No current or candidate version found for libapache-mod-python
Package: libapache-mod-python
State: not a real package



and then this:

> oliver@oliver-desktop:~$ sudo apt-get install libapache-mod-python
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libapache-mod-python is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache-mod-python has no installation candidate



I think there is something fundamentally wrong with my ubuntu or maybe where its getting packages from.

Any ideas?

Thanks again

O

---

### Post by faulkes on 2008-02-27
try

```

sudo apt-get update

```

Edit: ** Ignore the above **

I made a mistake below

use

```

aptitude show libapache2-mod-python 
sudo apt-get install libapache2-mod-python

```
 
Faulkes

---

