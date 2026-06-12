---
title: "Can't install PECL Poststript in Dapper server"
date: 2009-11-26
forum: Server Platforms
---

### Post by emyr42 on 2009-11-26
I have a VPS which runs 6.06 LTS.

Having googled, I've installed these:

php-pear
php5-dev
libgd2-xpm-dev
pslib1

php5-ps which I use on my Karmix office machine does not exist in the dapper repos (according to my apt output).

When I try to run

pecl install ps, I get this:

```
# pecl install ps
downloading ps-1.3.6.tgz ...
Starting to download ps-1.3.6.tgz (635,832 bytes)
................................done: 635,832 bytes
5 source files, building
running: phpize
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20050922
Zend Extension Api No:   220051025
path to pslib installation? : 
building in /var/tmp/pear-build-root/ps-1.3.6
running: /tmp/tmprRBlDg/ps-1.3.6/configure --with-ps=
checking for egrep... grep -E
checking for a sed that does not truncate output... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking whether gcc and cc understand -c and -o together... yes
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext
checking for PHP extension directory... /usr/lib/php5/20051025
checking for PHP installed headers prefix... /usr/include/php5
checking for re2c... no
configure: WARNING: You will need re2c 0.9.11 or later if you want to regenerate PHP parsers.
checking for gawk... gawk
checking for ps support... yes, shared
checking for ps files in default path... not found
configure: error: Please reinstall the pslib distribution
ERROR: `/tmp/tmprRBlDg/ps-1.3.6/configure --with-ps=' failed
#

```

As per other threads, I pressed enter when it asked for the pslib path. I've tried /usr/lib and /usr/share/pslib bit it still fails with the same messages.

---

