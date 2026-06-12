---
title: "phpMyAdmin Problems"
date: 2009-06-20
forum: Server Platforms
---

### Post by hermetic on 2009-06-20
I'm trying to set up a LAMP server for web development. I already have Apache2, PHP5, and MySQL installed. I attempted to install phpMyAdmin using the following code:

```
sudo apt-get install phpmyadmin
```

This seemed to work, but when I tried to go to [http://serverip/phpmyadmin](http://serverip/phpmyadmin) I received a 404 error. After trying  a few things I decided I would try to reinstall phpMyAdmin. This is where I think I made my mistake. I removed the /etc/phpmyadmin directory and all of it's contents. Now when I try to rerun the command above to install it again, I get the following:

```
 sudo apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
phpmyadmin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Nothing is installed. I tried removing the package with apt-get and reinstalling it, but it beings up this error:

```
 sudo apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  phpmyadmin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3612kB of archives.
After this operation, 13.4MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package phpmyadmin.
(Reading database ... 108505 files and directories currently installed.)
Unpacking phpmyadmin (from .../phpmyadmin_4%3a3.1.2-1_all.deb) ...
Setting up phpmyadmin (4:3.1.2-1) ...
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf
*** WARNING: ucf was run from a maintainer script that uses debconf, but
             the script did not pass --debconf-ok to ucf. The maintainer
             script should be fixed to not stop debconf before calling ucf,
             and pass it this parameter. For now, ucf will revert to using
             old-style, non-debconf prompting. Ugh!

             Please inform the package maintainer about this problem.
Replacing config file /etc/phpmyadmin/config-db.php with new version
dbconfig-common: flushing administrative password

```

The only thing now in /etc/phpmyadmin/ is this:

```
ls -la phpmyadmin/
total 20
drwxr-xr-x   2 root root      4096 2009-06-20 11:57 .
drwxr-xr-x 129 root root     12288 2009-06-20 11:57 ..
-rw-r-----   1 root www-data   553 2009-06-20 11:57 config-db.php

```

At this point I just want to completely remove everything having to do with phpMyAdmin and start over, but I'm at a loss as to how to even begin. Any help would be appreciated.

---

### Post by Kareeser on 2009-06-20
Ouch.

Try "sudo apt-get purge phpmyadmin".

---

### Post by Xanthomryr on 2009-06-20
Try ```
apt-get --purge remove phpmyadmin
``` this will remove phpmyadmin and its configuration in /etc.

After that, reinstall phpmyadmin again.

---

### Post by hermetic on 2009-06-20
Worked like a charm; thanks guys!

---

