---
title: "pecl install wbxml"
date: 2007-03-28
forum: The Cafe
---

### Post by phpist on 2007-03-28
hi everyone,
maybe this is not a releated category to post about wbxml but i dont really know which category is. i hope someone move this post to releated category if its not in already. anyway
i m running on Ubuntu 6.06 LTS - the Dapper Drake. as you can see i already installed libwbxml2 and php5-dev packages but i guess there is still something wrong.

**here is the problem :**

WARNING: channel "pear.php.net" has updated its protocols, use "channel-update pear.php.net" to update
downloading wbxml-1.0.0.tgz ...
Starting to download wbxml-1.0.0.tgz (4,506 bytes)
.....done: 4,506 bytes
3 source files, building
running: phpize
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20050922
Zend Extension Api No:   220051025
building in /var/tmp/pear-build-root/wbxml-1.0.0
running: /tmp/pear/cache/wbxml-1.0.0/configure
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
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for WBXML support... yes, shared
checking libexpat install prefix... no
checking for wbxml_conv_xml2wbxml_withlen in -lwbxml2... no
configure: error: failed to find and link against libwbxml2 ([http://libwbxml.aymerick.com/](http://libwbxml.aymerick.com/))
ERROR: `/tmp/pear/cache/wbxml-1.0.0/configure' failed

[B]any idea?
thank you[/B]

---

