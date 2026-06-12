---
title: "PHP breaks on Apache upgrade"
date: 2010-03-11
forum: Server Platforms
---

### Post by Samatva on 2010-03-11
On the recent upgrade to apache2 2.2.11-2ubuntu2.6, my 9.04 server could not start PHP:

```
apache2: Syntax error on line 184 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/apache2/modules/libphp5.so: cannot open shared object file: No such file or directory
```

RE-installing php5 package fixed it. I've had this happen on 2 boxes, one running auto updates scheduled via Webmin, the other broke on manually-started upgrade via Webmin.

On the box w/auto-update, first symptom was 500 Internal Server Error on all PHP pages.

Will try again in a bit on one of my VirtualBox installs...

All my Apache packages:
	apache2 2.2.11-2ubuntu2.6
	apache2-mpm-prefork 2.2.11-2ubuntu2.6
	apache2-utils 2.2.11-2ubuntu2.6	
	apache2.2-common 2.2.11-2ubuntu2.6
	libapache2-mod-auth-mysql 4.3.9-11
	libapache2-mod-perl2 2.0.4-5ubuntu1
	libapache2-reload-perl 0.10-2
	libapr1 1.2.12-5ubuntu0.1
	libaprutil1 1.2.12+dfsg-8ubuntu0.3

---

### Post by h'bel h'balim on 2010-03-11
I'm also having problems with the 2.2.11-2ubuntu2.6 upgrade.

I don't get any messages in my error log, but it's as if PHP is not installed: accessing index.php returns the .php file contents as a text file.

---

### Post by Samatva on 2010-03-11
Anyone know how to navigate the bug-reporting system?

---

### Post by h'bel h'balim on 2010-03-11
Ok,

When I re-enable the apache php module I get a similar error to Samatva.

When I grep the APT log I see ...

>   $ sudo grep php apt/term.log
  Removing php5-mysql ...
  Removing php5-gd ...
  Removing php5-curl ...
  Removing libapache2-mod-php5 ...
  Module php5 disabled.

... so the upgrade is not php-friendly!

I reinstalled the PHP5 package as per Samatva's instructions but I continued to get errors in my apache error.log ...

>    PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/curl.so' - /usr/lib/php5/20060613+lfs/curl.so: cannot open shared object file: No such file or directory in Unknown on line 0
   PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/gd.so' - /usr/lib/php5/20060613+lfs/gd.so: cannot open shared object file: No such file or directory in Unknown on line 0
   PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mysql.so' - /usr/lib/php5/20060613+lfs/mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0
   PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mysqli.so' - /usr/lib/php5/20060613+lfs/mysqli.so: cannot open shared object file: No such file or directory in Unknown on line 0
   PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/pdo_mysql.so' - /usr/lib/php5/20060613+lfs/pdo_mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0

... so I reinstalled php5-mysql, php5-gd, and php5-curl, and after restarting Apache (and my browser which had cached the rubbish) all is well.

---

### Post by Samatva on 2010-03-11
In my apt/term.log:

```
Removing libapache2-mod-php5 ...
Module php5 disabled.

```

No other php packages were affected. Re-installing the php5 package also restored libapache2-mod-php5

Not a big deal at all, but I won't be quite so glowing about how good Ubuntu updates are... They are still *way* better than any other distro I've used!!

---

### Post by Samatva on 2010-03-15
Further update:

Our production server had the same error when I updated it tonight. Was able to quickly re-install php5 package and be back up within about 2 minutes. 

My VirtualBox v 9.10 test/dev server upgraded without a glitch. 

For anyone able to pursue this, here's the apt log from my v9.04 "play" machine, wich had a scheduled upgrade @ 01:47 am, and I discovered/fixed it later in the day:

```
Log started: 2010-03-11  01:48:32
(Reading database ... 97441 files and directories currently installed.)
Preparing to replace apache2 2.2.11-2ubuntu2.5 (using .../apache2_2.2.11-2ubuntu2.6_all.deb) ...
Unpacking replacement apache2 ...
(Reading database ... 97440 files and directories currently installed.)
Removing websvn ...
Removing libphp-jpgraph ...
dpkg - warning: while removing libphp-jpgraph, directory `/usr/share/jpgraph' not empty so not removed.
Removing libapache2-mod-php5 ...
Module php5 disabled.
Run '/etc/init.d/apache2 restart' to activate new configuration!
Removing apache2-mpm-prefork ...
 * Stopping web server htcacheclean
 ... waiting .   ...done.
(Reading database ... 97239 files and directories currently installed.)
Preparing to replace apache2.2-common 2.2.11-2ubuntu2.5 (using .../apache2.2-common_2.2.11-2ubuntu2.6_i386.deb) ...
Unpacking replacement apache2.2-common ...
Selecting previously deselected package apache2-mpm-worker.
Unpacking apache2-mpm-worker (from .../apache2-mpm-worker_2.2.11-2ubuntu2.6_i386.deb) ...
Processing triggers for ufw ...
Processing triggers for man-db ...
Setting up apache2.2-common (2.2.11-2ubuntu2.6) ...

Setting up apache2-mpm-worker (2.2.11-2ubuntu2.6) ...
 * Starting web server apache2
   ...done.

Setting up apache2 (2.2.11-2ubuntu2.6) ...
Log ended: 2010-03-11  01:48:58

Log started: 2010-03-11  01:49:20
dpkg: apache2-mpm-worker: dependency problems, but removing anyway as you request:
 apache2 depends on apache2-mpm-worker (>= 2.2.11-2ubuntu2.6) | apache2-mpm-prefork (>= 2.2.11-2ubuntu2.6) | apache2-mpm-event (>= 2.2.11-2ubuntu2.6); however:
  Package apache2-mpm-worker is to be removed.
  Package apache2-mpm-prefork is not installed.
  Package apache2-mpm-event is not installed.
(Reading database ... 97247 files and directories currently installed.)
Removing apache2-mpm-worker ...
 * Stopping web server htcacheclean
 ... waiting    ...done.
Selecting previously deselected package apache2-mpm-prefork.
(Reading database ... 97239 files and directories currently installed.)
Unpacking apache2-mpm-prefork (from .../apache2-mpm-prefork_2.2.11-2ubuntu2.6_i386.deb) ...
Setting up apache2-mpm-prefork (2.2.11-2ubuntu2.6) ...
 * Starting web server apache2
   ...done.

Log ended: 2010-03-11  01:49:26

Log started: 2010-03-11  01:49:48
(Reading database ... 97248 files and directories currently installed.)
Preparing to replace apache2-utils 2.2.11-2ubuntu2.5 (using .../apache2-utils_2.2.11-2ubuntu2.6_i386.deb) ...
Unpacking replacement apache2-utils ...
Processing triggers for man-db ...
Setting up apache2-utils (2.2.11-2ubuntu2.6) ...
Log ended: 2010-03-11  01:49:50

Log started: 2010-03-11  01:50:36
(Reading database ... 97248 files and directories currently installed.)
Preparing to replace dpkg 1.14.24ubuntu1 (using .../dpkg_1.14.24ubuntu1.1_i386.deb) ...
Unpacking replacement dpkg ...
Processing triggers for man-db ...
Setting up dpkg (1.14.24ubuntu1.1) ...

Log ended: 2010-03-11  01:50:44

Log started: 2010-03-11  01:51:09
(Reading database ... 97248 files and directories currently installed.)
Preparing to replace dpkg-dev 1.14.24ubuntu1 (using .../dpkg-dev_1.14.24ubuntu1.1_all.deb) ...
Unpacking replacement dpkg-dev ...
Processing triggers for man-db ...
Setting up dpkg-dev (1.14.24ubuntu1.1) ...
Log ended: 2010-03-11  01:51:13

Log started: 2010-03-11  01:51:37
(Reading database ... 97248 files and directories currently installed.)
Preparing to replace tzdata 2009u~repack-0ubuntu9.04 (using .../tzdata_2010e~repack-0ubuntu9.04_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2010e~repack-0ubuntu9.04) ...

Current default timezone: 'America/New_York'
Local time is now:      Thu Mar 11 01:51:40 EST 2010.
Universal Time is now:  Thu Mar 11 06:51:40 UTC 2010.
Run 'dpkg-reconfigure tzdata' if you wish to change it.


Log ended: 2010-03-11  01:51:41

Log started: 2010-03-11  12:31:10
Selecting previously deselected package libapache2-mod-php5.
(Reading database ... 97295 files and directories currently installed.)
Unpacking libapache2-mod-php5 (from .../libapache2-mod-php5_5.2.6.dfsg.1-3ubuntu4.5_i386.deb) ...
Selecting previously deselected package php5.
Unpacking php5 (from .../php5_5.2.6.dfsg.1-3ubuntu4.5_all.deb) ...
Setting up libapache2-mod-php5 (5.2.6.dfsg.1-3ubuntu4.5) ...
 * Reloading web server config apache2

Setting up php5 (5.2.6.dfsg.1-3ubuntu4.5) ...
Log ended: 2010-03-11  12:31:22

```

---

