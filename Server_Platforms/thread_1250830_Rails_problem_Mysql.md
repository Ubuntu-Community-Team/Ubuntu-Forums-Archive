---
title: "Rails problem Mysql"
date: 2009-08-27
forum: Server Platforms
---

### Post by bperucchi on 2009-08-27
I'm having this problem to install the gem of mysql . Does someone know what I should do ? I already instaled all lib of mysql

breno@breno-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty
breno@breno-desktop:~$ uname -a
Linux breno-desktop 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 01:19:55 UTC 2009 x86_64 GNU/Linux

breno@breno-desktop:~$ ruby -v
ruby 1.8.7 (2008-08-11 patchlevel 72) [x86_64-linux]
breno@breno-desktop:~$ gem -v
1.3.4
breno@breno-desktop:~$ rails -v
Rails 2.3.3 


ruby 1.8.7 (2008-08-11 patchlevel 72) [x86_64-linux]
breno@breno-desktop:~$ sudo gem install mysql
Building native extensions.  This could take a while...
ERROR:  Error installing mysql:
        ERROR: Failed to build gem native extension.

[B]/usr/bin/ruby1.8 extconf.rb
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lm... yes
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lz... yes
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lsocket... no
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lnsl... yes
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lmygcc... no
checking for mysql_query() in -lmysqlclient... no
*** extconf.rb failed ***[/B]
Could not create Makefile due to some reason, probably lack of
necessary libraries and/or headers.  Check the mkmf.log file for more
details.  You may need configuration options.



breno@breno-desktop:~$ dpkg -l|grep mysql
ii  libapache2-mod-auth-mysql                  4.3.9-11                           Apache 2 module for MySQL authentication
ii  libdataobjects-mysql-ruby1.8               0.2.4-2                            MySQL adapter for libdataobjects-ruby1.8
ii  libdbd-mysql-perl                          4.008-1                            A Perl5 database interface to the MySQL data
ii  libdbd-mysql-ruby                          0.2.2-1                            Ruby/DBI driver for MySQL
ii  libdbd-mysql-ruby1.8                       0.2.2-1                            Ruby/DBI MySQL driver for Ruby 1.8
ii  libmysql-ruby                              2.7.4-1                            MySQL module for Ruby
ii  libmysql-ruby1.8                           2.7.4-1                            MySQL module for Ruby 1.8
ii  libmysqlclient15off                        5.1.30really5.0.75-0ubuntu10.2     MySQL database client library
ii  mysql-client                               5.1.30really5.0.75-0ubuntu10.2     MySQL database client (metapackage depending
ii  mysql-client-5.0                           5.1.30really5.0.75-0ubuntu10.2     MySQL database client binaries
ii  mysql-common                               5.1.30really5.0.75-0ubuntu10.2     MySQL database common files
ii  mysql-server                               5.1.30really5.0.75-0ubuntu10.2     MySQL database server (metapackage depending
ii  mysql-server-5.0                           5.1.30really5.0.75-0ubuntu10.2     MySQL database server binaries
ii  mysql-server-core-5.0                      5.1.30really5.0.75-0ubuntu10.2     MySQL database core server files
ii  php5-mysql                                 5.2.6.dfsg.1-3ubuntu4.2            MySQL module for php5

---

