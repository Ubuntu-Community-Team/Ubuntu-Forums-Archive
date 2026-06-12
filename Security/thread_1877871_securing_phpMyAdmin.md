---
title: "securing phpMyAdmin"
date: 2011-11-08
forum: Security
---

### Post by sneakyimp on 2011-11-08
I've just installed phpmyadmin:
```
apt-get install phpmyadmin
```

I'm fairly disappointed with the result for a few reasons:
* no explanation is really provided for dbconfig-common installation when the option is presented at install time.  i have no idea what this means for security or convenience.  
* installs for non-SSL access (i.e., access if via HTTP, not HTTPS)
* configuration is complicated due to inclusion of numerous configuration files -- why is this?
* installs binaries in /usr/sbin folder
* setup subdirectory?  installation instructions?  what is left to configure? is setup subdirectory configured to alter the correct configuration file of the 4 on my file system?
* I get '403 forbidden' when trying to access [www.mydomain.com/phpmyadmin](www.mydomain.com/phpmyadmin)

I believe I can figure out the HTTPS vs. HTTP access, but I'm wondering what on earth is the reason for all of the config.inc.php files?  there appear to be a bunch of them and I'm not sure *why* they exist or where my changes should be made, if any:
```

/var/lib/phpmyadmin/config.inc.php
/etc/phpmyadmin/config.inc.php
/usr/share/phpmyadmin/config.inc.php
/usr/share/phpmyadmin/setup/frames/config.inc.php

```

And what about the binaries this creates in the /usr/sbin folder:
```

/usr/sbin/pma-configure
/usr/sbin/pma-secure

```

Do I need to run these? Have they been run already? Do they present a security risk?

And lastly, I would only like phpmyadmin to provide access to one particular database server which is *not hosted on this machine*.  The machine running MySQL does not have apache installed.

---

### Post by c.cobb on 2011-11-08
Yeah, phpMyAdmin is "disappointing" ... that's putting it mildly :)

You might want to toss phpMyAdmin and try some better tools. The ISP where I have my blog only supports phpMyAdmin and they won't answer questions about using anything better, but it drove me nuts. After some googling, I finally figured out how to use SSH port-forwarding to allow using far better apps. 

I really like **MySQL Admin** and **MySQL Query Browser**, but these are older, unsupported, and it's recommended that you use **MySQL WorkBench** instead--which bundles the other two separate apps into one big, cumbersome window and adds some other developer stuff that I don't use.

**Using SSH port-forwarding**, you can set up a proxy on your local machine that will support either of two scenarios: 1) where the MySQL server is running directly on the remote host, or 2) where you must login to a remote machine first and then connect to a secondary MySQL server. The example scripts below work for both and, as I have two ISPs, these are taken from scripts that work for me.

If using MySQL Admin / QueryBrowser, use you need to use one of the script examples below to create an SSH port forward / proxy connection. Get started with the 'Backup' and 'Catalogs' menu choices on the left-hand side of the Admin tool.

If using WorkBench, you can use the 'Manage Connections' menu (on SQL Development side) for Query/Browser connections, and "Manage Server Instances" menu (on Server Administration side) for Admin connections. Dunno why they can't use the same setup, and they can't even use the same format for the setup forms. However, what is nice is that you can save connection configs for multiple MySQL servers.

Either way, you can then use the following for the MySQL server and port:

Desktop/Laptop Local Host
.   MySQL Server Hostname:   127.0.0.1
.   MySQL Server port num:    3307       # so no conflicts if MySQL running locally
.   MySQL Database username:
.   MySQL Database password:

This would be a nice topic to do a comprehensive write up for as the first time set up is nasty but, once you get it working, it's very handy to know how to do.



**Port forwarding scripts** for use with MySQL Admin / Query Browser. You only need the last line of each that runs the 'ssh' command -- the rest is just fluff.

Remote Example 1: SSH login to access MySQL running on remote host

```
#!/bin/bash
#
echo "Forwarding to DOMAIN1.com on port 3307"
echo "Use '127.0.0.1' for the remote DB Server name"

xterm \
  -title "MySQL -- DOMAIN1.com on port 3307 -- use 127.0.0.1 as DB server" \
  -geometry 120x5+20-40 \
  -r -e /bin/bash -l -c \
    "ssh -L 3307:localhost:3306 DOMAIN_USER1@DOMAIN1.com" &
```Remote Example 2: SSH login to forward to another MySQL server

```
#!/bin/bash
# Set up SSH port forwarding for MySQL Admin and MySQL Query Browser.
# These are far nicer to use than phpMyAdmin or other ISP provided tools.
#
echo "Forwarding to mysql-DOMAIN2.com on port 3307"
echo "Use '127.0.0.1' for remote DB Server name"

xterm -title "MySQL -- DOMAIN2.com on port 3307 -- use 127.0.0.1 as DB server" \
      -geometry 120x5+20-40 \
      -r -e /bin/bash -l -c \
         "ssh -L 3307:mysql-DOMAIN2.com:3306 DOMAIN_USER2@DOMAIN2.com" &
```**Installing the apps** -- if you're not familiar with SSH port forwarding, might want to try using the Admin and Query Browser apps, as WorkBench SSH connections are confusing to configure (at least in version 5.2.34). 

I installed WorkBench back in June on Lucid so some things may have changed. If so, please let me know.

**MySQL Query Browser, and MySQL Admin**
. use the older unsupported package, not the new stuff
   in Synaptic Package Manager, select
   - mysql-client, and mysql-admin

Simple, lightweight, and easy to use. However, is older, unsupported, and some operations can cause it to crash. 


**MySQL WorkBench**  
.  add a few small dependencies, including
   -  libctemplate0, libzpl, python-paramiko, python-pysqlite2
.  already Installed:  mysql-client, python-crypto

Big, complex, and powerful. This is nice because you can set up the SSH proxy / forwarding and it's stored in an XML config file. However, the setup is complicated unless (or even if) you're familiar with SSH port forwarding.

---

