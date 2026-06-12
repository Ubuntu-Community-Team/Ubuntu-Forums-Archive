---
title: "installing gd2 for php on breezy badger"
date: 2006-06-08
forum: Server Platforms
---

### Post by Jrdgames on 2006-06-08
Hi,
I would like to install gd2 on my server.

I have  php4 and 5 installed im using apache2 for my webserver and ISPConfig for a control panel.

Can someone please tell me how to install gd2 and what other packages I may need?

---

### Post by jgoguen on 2006-06-08
Run ```
sudo apt-get install php5-gd
``` and agree to any extra packages it wants to install.

---

### Post by Jrdgames on 2006-06-08
Thankyou for the fast reply, I've ran that but it didn't ask to install any extra packages. Did this install the latest version (gd2) or just gd?

I've made a file with phpinfo() and then search for gd but all I see is gdbm
> dba
DBA support 	enabled
Supported handlers 	gdbm cdb cdb_make db4 inifile flatfile
which does not seem to be an entry for gd.

---

### Post by jgoguen on 2006-06-09
I can't load your phpinfo page.  That's probably a Good Thing(tm) though, call me paranoid but it's not something I'd want to let the world see :)

Check for the existence of the file "/usr/lib/php5/20051025/gd.so" and check in Synaptic that the package libgd2-xpm is installed (included with php5-gd, so it should be installed).  Or if you're a CLI person,```
apt-cache --installed search libgd2-xpm
``` will do it too.  If that's there I don't think you'll have any problems using GD programs.  If you want to make sure you have the GD2 libraries, you can install them too ```
sudo apt-get install libgd2 libgd2-dev
```  That should ask for additional packages (and will also include the libgd2-xpm package) and will give you much more than I have installed to run a [GD2 photo album]("http://iapetus.dyndns.org/scry/").

---

### Post by linuxone on 2006-06-09
Hi,

[QUOTE=Jrdgames]Thankyou for the fast reply, I've ran that but it didn't ask to install any extra packages. Did this install the latest version (gd2) or just gd?[/QUOTE]

the gd lib is activated into the php.ini file by this line:

extension=gd.so

Depending on your php version you can find php.ini in:

/etc/php4/apache2/php.ini
/etc/php5/apache2/php.ini

Open the ini file with your favorite editor (ie.: sudo vi /etc/php4/apache2/pp.ini), search for this line and check if this config option is enabled. Means: no semicolon into the first row. If there is a semicolon, remove it, save the ini file and restart apache.

> I've made a file with phpinfo() and then search for gd but all I see is gdbm which does not seem to be an entry for gd.

if gd is enabled, it'll appear into an own table like exif, ftp, ...

But you should never, really never publish a phpinfo result to the public. This opens to much internal details about your entire server to everyone. These internal details should be keep as a secret.

Thomas

---

### Post by Jrdgames on 2006-06-11
Thanks for the replies everyone
> 
Check for the existence of the file "/usr/lib/php5/20051025/gd.so" 
I go into /usr/lib/php5 and theres a folder called 20041030 and its empty, I go to /usr/lib/php4 and theres a folder called 20050606 and it has .so files in it but no gd,so

> and check in Synaptic that the package libgd2-xpm is installed (included with php5-gd, so it should be installed). Or if you're a CLI person,
Code:

apt-cache --installed search libgd2-xpm

will do it too. If that's there I don't think you'll have any problems using GD programs. If you want to make sure you have the GD2 libraries, you can install them too
Code:

sudo apt-get install libgd2 libgd2-dev

That should ask for additional packages (and will also include the libgd2-xpm package)

I have done all this but I still dont see gd on phpinfo.

> the gd lib is activated into the php.ini file by this line:

extension=gd.so

Depending on your php version you can find php.ini in:

/etc/php4/apache2/php.ini
/etc/php5/apache2/php.ini

Open the ini file with your favorite editor (ie.: sudo vi /etc/php4/apache2/pp.ini), search for this line and check if this config option is enabled. Means: no semicolon into the first row. If there is a semicolon, remove it, save the ini file and restart apache.

I have changed

;extension=gd.so
to
extension=gd.so

restart apache but it still doesn't show up,

> But you should never, really never publish a phpinfo result to the public. This opens to much internal details about your entire server to everyone. These internal details should be keep as a secret.
hehe sorry didn't know thanks for telling me.

---

### Post by linuxone on 2006-06-11
Hi,

[QUOTE=Jrdgames]I have changed
;extension=gd.so
to
extension=gd.so
restart apache but it still doesn't show up,[/QUOTE]

if you really have installed all required libraries (most important: **php4-gd**) and enabled the extention as mentioned above, gd must by available with the next apache restart.

Did you check the apache error log (/var/log/apache2/) for error messages?

Thomas

---

### Post by Jrdgames on 2006-06-11
I found this error:
> PHP Warning:  Unknown(): Unable to load dynamic library '/usr/lib/php4/20050606/gd.so' - /usr/lib/php4/20050606/gd.so: cannot open shared object file: No such file or directory in Unknown on line 0

I just looked through my synaptic and found i didn't have php4-gd and php5-gd installed so i installed those and restarted apache now gd shows up

---

