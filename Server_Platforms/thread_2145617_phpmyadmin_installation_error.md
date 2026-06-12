---
title: "phpmyadmin installation error"
date: 2013-05-16
forum: Server Platforms
---

### Post by Chris Jerome on 2013-05-16
Hi, 

I installed phpmyadmin on my system and it was working fine, but I did not like that the password I had given it (same as my user password) was in plain text in one of the configuration files, and I could not find how to change that, so I uninstalled and attempted to reinstall. To cut a long story short, now if I try to reinstall phpadmin I get the error: "could not open configuration file /etc/apache2/conf.d/phpmyadmin.conf: no such file or directory", followed by: "invoke-rc.d: initscript apache2, action "reload" failed". I get the same error if I run dpkg-reconfigure phpmyadmin. The file phpmyadmin.conf is a symbolic link to etc/phpmyadmin/apache.conf. However, the phpmyadmin folder only contains the file config-db.php. I have tried deleting the symbolic link and the phpmyadmin folder before reinstalling, but the problem just recurs.

Since I did not get this error on the original install, I guessed that there was some configuration file hanging around from that install that was causing this error, but I have looked at all the files created in /etc in the last day and cannot find the culprit.

I would appreciate any help with figuring out how to fix this problem.

Thanks!
Chris

---

### Post by Chris Jerome on 2013-05-16
OK, so I am trying to fix this problem and decided to remove and reinstall php and mysql.

So I used:
sudo apt-get remove php5-mysql libapache2-mod-php5 mysql-server
sudo apt-get purge php5-mysql libapache2-mod-php5 mysql-server
sudo apt-get install php5-mysql libapache2-mod-php5 mysql-server

Now mysql runs, but php will not start, I get the errors: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/gd.so', and Unable to load dynamic library '/usr/lib/php5/20090626+lfs/mcrypt.so'

Sure enough those files are missing from that directory. I have checked both php.ini files that I can find on the system and neither references those files, so I don't know why it is looking for them and/or why they are missing.

This is driving me crazy, I had a great running webserver yesterday morning, now I can't get anything to work. Any help would be greatly appreciated.

Thanks,
Chris

---

### Post by steeldriver on 2013-05-16
well these are the php5 subpackages present on my 'play' server

```
$ dpkg -l | grep php5
ii  libapache2-mod-php5                5.3.10-1ubuntu3.6            server-side, HTML-embedded scripting language (Apache 2 module)
ii  php5-cli                           5.3.10-1ubuntu3.6            command-line interpreter for the php5 scripting language
ii  php5-common                        5.3.10-1ubuntu3.6            Common files for packages built from the php5 source
ii  php5-gd                            5.3.10-1ubuntu3.6            GD module for php5
ii  php5-mcrypt                        5.3.5-0ubuntu1               MCrypt module for php5
ii  php5-mysql                         5.3.10-1ubuntu3.6            MySQL module for php5

```

Maybe check if they're all present and if not, try installing (or re-installing) php5-gd and php5-mcrypt as well?

---

### Post by Chris Jerome on 2013-05-17
Thanks!

I got the same result you did to the dpkg command, but went ahead and installed php5-gd and php5-mcrypt. The missing files were installed and now php is working. Thanks so much - I am teaching myself the whole LAMP thing from books and the web, so I know just enough to be dangerous - it is great to have this resource available. Now to see if I can get phpmyadmin working...

Chris

---

