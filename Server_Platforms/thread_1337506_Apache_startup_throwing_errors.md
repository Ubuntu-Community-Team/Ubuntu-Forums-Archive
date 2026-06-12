---
title: "Apache startup throwing errors"
date: 2009-11-25
forum: Server Platforms
---

### Post by breauxlg on 2009-11-25
I've got 8.04 lts installed with a lamp configuration and ispconfig. I loaded a drupal website and could not get images to show on the web site. After working with Drupal techs, found that it seems to be a problem on the Apache server side. I looked at the apache startup log and it's showing a number of errors. Don't know if they are related to the problem or not, but I'd appreciate any guidance or information. Here's the log:
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/pdo_sqlite.so' - /usr/lib/php5/20060613+lfs/pdo_sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/sqlite.so' - /usr/lib/php5/20060613+lfs/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Sun Nov 22 07:57:40 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.11-0.dotdeb.1 with Suhosin-Patch mod_ruby/1.2.6 Ruby/1.8.6(2007-09-24) mod_ssl/2.2.8 OpenSSL/0.9.8g configured -- resuming normal operations
[Sun Nov 22 07:57:40 2009] [warn] long lost child came home! (pid 23214)
[Sun Nov 22 11:39:47 2009] [error] [client 61.160.216.63] File does not exist: /var/www/sharedip/prx2.php
[Sun Nov 22 21:51:32 2009] [error] [client 72.30.78.251] File does not exist: /var/www/sharedip/robots.txt
[Mon Nov 23 13:01:37 2009] [error] [client 61.160.216.63] File does not exist: /var/www/sharedip/prx2.php
[Mon Nov 23 15:47:00 2009] [error] [client 194.72.238.62] Invalid method in request \x16\x03
[Tue Nov 24 15:11:46 2009] [error] [client 61.160.216.63] File does not exist: /var/www/sharedip/prx2.php
[Tue Nov 24 16:43:42 2009] [error] [client 194.72.238.62] Invalid method in request \x16\x03\x01
[Wed Nov 25 12:14:59 2009] [error] [client 65.55.230.164] File does not exist: /var/www/sharedip/robots.txt
[Wed Nov 25 13:34:21 2009] [notice] caught SIGWINCH, shutting down gracefully
[Wed Nov 25 13:46:11 2009] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/pdo_sqlite.so' - /usr/lib/php5/20060613+lfs/pdo_sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/sqlite.so' - /usr/lib/php5/20060613+lfs/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Wed Nov 25 13:46:14 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.11-0.dotdeb.1 with Suhosin-Patch mod_ruby/1.2.6 Ruby/1.8.6(2007-09-24) mod_ssl/2.2.8 OpenSSL/0.9.8g configured -- resuming normal operations
[Wed Nov 25 13:46:17 2009] [notice] caught SIGWINCH, shutting down gracefully
[Wed Nov 25 13:46:28 2009] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/pdo_sqlite.so' - /usr/lib/php5/20060613+lfs/pdo_sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/sqlite.so' - /usr/lib/php5/20060613+lfs/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Wed Nov 25 13:46:28 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.11-0.dotdeb.1 with Suhosin-Patch mod_ruby/1.2.6 Ruby/1.8.6(2007-09-24) mod_ssl/2.2.8 OpenSSL/0.9.8g configured -- resuming normal operations

---

### Post by Vegan on 2009-11-25
Looks like some errors in the documents. Did they work before? Or is this a new problem?

---

### Post by breauxlg on 2009-11-28
I have not gotten this to work yet. This is a pretty new install, so there well could be something wrong that has been wrong since the  install.

---

