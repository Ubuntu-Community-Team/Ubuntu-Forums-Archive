---
title: "mysql gem fails to install using Ruby 1.9.1"
date: 2009-03-30
forum: Server Platforms
---

### Post by destiney on 2009-03-30
This issue exists for Ubuntu 9.04beta, but not 8.10.


I can't get the MySQL gem to install using Ruby 1.9.1.

> gem install mysql -- --with-mysql-config=/usr/bin/mysql_config
Building native extensions.  This could take a while...
ERROR:  Error installing mysql:
       ERROR: Failed to build gem native extension.

/usr/local/bin/ruby extconf.rb install mysql --
--with-mysql-config=/usr/bin/mysql_config
checking for mysql_ssl_set()... yes
checking for mysql.h... yes
creating Makefile

make
gcc -I. -I/usr/local/include/ruby-1.9.1/i686-linux
-I/usr/local/include/ruby-1.9.1/ruby/backward
-I/usr/local/include/ruby-1.9.1 -I. -DHAVE_MYSQL_SSL_SET
-DHAVE_MYSQL_H  -D_FILE_OFFSET_BITS=64  -I/usr/include/mysql
-DBIG_JOINS=1 -fPIC -fno-strict-aliasing -fPIC  -O2 -g -Wall
-Wno-parentheses  -o mysql.o -c mysql.c
mysql.c:6:21: error: version.h: No such file or directory
[...]
make: *** [mysql.o] Error 1

Gem files will remain installed in
/usr/local/lib/ruby/gems/1.9.1/gems/mysql-2.7 for inspection.
Results logged to /usr/local/lib/ruby/gems/1.9.1/gems/mysql-2.7/gem_make.out


My Ruby is installed from source:

> ruby -v
ruby 1.9.1p0 (2009-01-30 revision 21907) [i686-linux]


My MySQL is installed from packages:

> dpkg -l|grep mysql
ii  libmysqlclient15-dev              5.1.30really5.0.75-0ubuntu9
 MySQL database development files
ii  libmysqlclient15off               5.1.30really5.0.75-0ubuntu9
 MySQL database client library
ii  mysql-client-5.0                  5.1.30really5.0.75-0ubuntu9
 MySQL database client binaries
ii  mysql-common                      5.1.30really5.0.75-0ubuntu9
 MySQL database common files


My mysql_config exists and seems to work:

> /usr/bin/mysql_config
Usage: /usr/bin/mysql_config [OPTIONS]
Options:
       --cflags         [-I/usr/include/mysql  -DBIG_JOINS=1 -fPIC
-fno-strict-aliasing]
       --include        [-I/usr/include/mysql]
       --libs           [-Wl,-Bsymbolic-functions -rdynamic
-L/usr/lib/mysql -lmysqlclient]
       --libs_r         [-Wl,-Bsymbolic-functions -rdynamic
-L/usr/lib/mysql -lmysqlclient_r]
       --socket         [/var/run/mysqld/mysqld.sock]
       --port           [0]
       --version        [5.0.75]
       --libmysqld-libs [-Wl,-Bsymbolic-functions -rdynamic
-L/usr/lib/mysql -lmysqld -lwrap -lrt]


And finally, I have several version.h files:

> locate version.h
/usr/include/linux/version.h
/usr/include/linux/dvb/version.h
/usr/src/ruby-1.9.1-p0/version.h

---

### Post by mattyB on 2009-04-11
I am having an identical problem.  I'm curious about what the solution is.

---

### Post by mattyB on 2009-04-14
I was able to resolve this on my system by uninstalling Ruby 1.9.1 and reverting back to Ruby 1.8.7.  I downloaded and compiled the tarball including gems.  I was then able to install mysql via the gems.
Frustrating, but such is life.

My

---

### Post by gard76 on 2009-04-16
I solved it on Jaunty using this link: [http://frozenplague.net/2009/01/ruby-191-rubygems-rails/](http://frozenplague.net/2009/01/ruby-191-rubygems-rails/)

---

