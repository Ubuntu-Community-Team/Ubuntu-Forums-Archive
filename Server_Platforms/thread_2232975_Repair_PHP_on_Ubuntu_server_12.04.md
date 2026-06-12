---
title: "Repair PHP on Ubuntu server 12.04"
date: 2014-07-05
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2014-07-05
Hi all

Had an 'incident' on this server and am now receiving messages such as follows.
> PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/intl.so' - /usr/lib/php5/20090626/intl.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/pdo_pgsql.so' - /usr/lib/php5/20090626/pdo_pgsql.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/pdo_sqlite.so' - /usr/lib/php5/20090626/pdo_sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/pgsql.so' - /usr/lib/php5/20090626/pgsql.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/sqlite3.so' - /usr/lib/php5/20090626/sqlite3.so: cannot open shared object file: No such file or directory in Unknown on line 0
Any ideas as to how resolve the issue(s), please?

TIA

---

### Post by CharlesA on 2014-07-05
See here:
[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/875262](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/875262)

What version of Ubuntu and what version of php is installed?

---

### Post by ChrisRChamberlain on 2014-07-05
CharlesA

Thanks for your reply and link

Ubuntu server 12.04. LTS
PHP Version 5.3.10-1ubuntu3.12

---

### Post by ChrisRChamberlain on 2014-07-07
Reinstalled ownCloud which had been installed and later purged.

Messages have stopped.

---

