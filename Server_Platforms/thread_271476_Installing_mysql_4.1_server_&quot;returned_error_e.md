---
title: "Installing mysql 4.1 server &quot;returned error exit status 1&quot;"
date: 2006-10-04
forum: Server Platforms
---

### Post by ecotrope on 2006-10-04
I'm running Dapper Drake on an i386 system. Apache 2.0.55 is installed and running fine. Everything works great except for this little headache. I am trying to set up a CivicSpace/Drupal demo system, which requires the earlier versions of MySQL and PHP (MySQL 4.1, PHP 4.4).

Of course, I didn't realize that CivicSpace didn't run on the current versions (MySQL 5.0.22, PHP 5.1.2) until after I installed them with the Synaptic Package Manager. Subsequently, I uninstalled, added the Universe repository and attempted to install the earlier versions. PHP4.4.2-1build1 is installed and working with Apache but I can't get MySQL 4.1 to install with Synaptic or bash. Here is the message that I get:

[INDENT]    sudo apt-get install mysql-server-4.1
    Password:
    Reading package lists... Done
    Building dependency tree... Done
    The following NEW packages will be installed:
    mysql-server-4.1
    0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
    Need to get 0B/17.0MB of archives.
    After unpacking 38.1MB of additional disk space will be used.
    Preconfiguring packages ...
    (Reading database ... 74360 files and directories currently installed.)
    Unpacking mysql-server-4.1 (from .../mysql-server-4.1_4.1.15-1ubuntu5_i386.deb) ...
    Aborting downgrade from (at least) 5.0 to 4.1.
    dpkg: error processing /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb (--unpack):
    [B]subprocess pre-installation script returned error exit status 1
    Errors were encountered while processing:
    /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb
    E: Sub-process /usr/bin/dpkg returned an error code (1)[/INDENT]
[/B]
I don't know if this has something to do with the earlier installation or the repositories or a conflicting installation. I tried uninstalling everything related to MySQL but that didn't seem to help.  It's not an issue of disk space since I have 10 gb free. Can somebody please guide me in the right direction?

---

### Post by sandbox2003 on 2006-10-16
I search the internet, and somebody said that maybe you should do "rm /var/lib/mysql -rf" before your downgrade from 5.0 to 4.1. I tried, and it worked well.

---

### Post by ecotrope on 2006-10-16
Thank you, Sandbox2003.  That sounds plausible.  I ended up having to reinstall Ubuntu sice I didn't know what was causing the conflict.  I didn't istall mysql 5.0 this time and it worked without any problem.

---

### Post by dorre on 2006-10-20
Had the same problem. That seemed do to the trick. thanks!

---

