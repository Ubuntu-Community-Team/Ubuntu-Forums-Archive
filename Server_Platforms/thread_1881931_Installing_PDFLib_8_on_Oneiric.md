---
title: "Installing PDFLib 8 on Oneiric"
date: 2011-11-16
forum: Server Platforms
---

### Post by flickerfly on 2011-11-16
I'm getting a strange error from the configure script when installing PDFLib 8 through pecl on Ubuntu Oneiric Server.  I don't know if I'm missing a dependency or am having some other problem. I've tried installing PDFLib 7 also and get the same error.

> checking for PDF_open_pdi in -lpdf... no
configure: error:
PDFlib extension requires at least pdflib 4.0.x.

Here is the details of how I'm doing the failed install:

```
$ cd /usr/local/src/
$ wget [http://www.pdflib.com/binaries/PDFlib/803/PDFlib-8.0.3-Linux-x86_64-C-C++.tar.gz](http://www.pdflib.com/binaries/PDFlib/803/PDFlib-8.0.3-Linux-x86_64-C-C++.tar.gz)
$ tar zxvf PDFlib-8.0.3-Linux-x86_64-php.tar.gz
$ sudo apt-get install php-pear
$ sudo apt-get install php5-dev
$ sudo apt-get install build-essentials checkinstall
$ sudo apt-get install re2c
$ sudo pecl install pdflib
```

When asked for the "path to pdflib installation:" I enter...
/usr/local/src/PDFlib-8.0.3-Linux-x86_64-C-C++/bind/c

It responds with this:
> building in /tmp/pear/temp/pear-build-rootYIeYUh/pdflib-2.1.8
running: /tmp/pear/temp/pdflib/configure
--with-pdflib=/usr/local/src/PDFlib-8.0.3-Linux-x86_64-C-C++/bind/c
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for cc... cc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables...
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether cc accepts -g... yes
checking for cc option to accept ISO C89... none needed
checking how to run the C preprocessor... cc -E
checking for icc... no
checking for suncc... no
checking whether cc understands -c and -o together... yes
checking for system library directory... lib
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main
-I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext
-I/usr/include/php5/ext/date/lib
checking for PHP extension directory... /usr/lib/php5/20090626
checking for PHP installed headers prefix... /usr/include/php5
checking if debug is enabled... no
checking if zts is enabled... no
checking for re2c... re2c
checking for re2c version... 0.13.5 (ok)
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for PDFlib support... yes, shared
checking for PDF_open_pdi in -lpdf... no
configure: error:
PDFlib extension requires at least pdflib 4.0.x.
See config.log for more information.

ERROR: `/tmp/pear/temp/pdflib/configure
--with-pdflib=/usr/local/src/PDFlib-8.0.3-Linux-x86_64-C-C++/bind/c' failed

---

### Post by flickerfly on 2011-11-16
So I found out that I can simply use the binaries they provide and went this method instead. You have to download them in a separate package specifically for PHP.

For Detail See: [http://tech.groups.yahoo.com/group/pdflib/message/21517](http://tech.groups.yahoo.com/group/pdflib/message/21517)

---

