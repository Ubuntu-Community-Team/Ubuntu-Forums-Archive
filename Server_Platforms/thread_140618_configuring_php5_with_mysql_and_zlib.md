---
title: "configuring php5 with mysql and zlib"
date: 2006-03-06
forum: Server Platforms
---

### Post by madubuntuer on 2006-03-06
checking whether to enable LIBXML support... yes
checking libxml2 install dir... no
checking for xml2-config path... /usr/bin/xml2-config
checking whether libxml build works... yes
checking for OpenSSL support... no
checking for Kerberos support... no
checking for PCRE support... yes
checking for ZLIB support... yes
checking if the location of ZLIB install directory is defined... no
configure: error: Cannot find libz

I cant find libz package any where 
what am I doing wrong?

heres what I used to compile 
./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql --with-zlib=/usr/include

tried but didn't recognise zlib
./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql --with-zlib=/usr

---

### Post by duds on 2006-03-14
Yeah, I am having the same problem installing my MYSQL. My output is shown below and I don't know how to install libz-devel in Ubuntu. Help?

OUPUT

An error occurred while linking the DBD::mysql driver. The error
message seems to indicate that you don't have a libz.a,
or a libz.so. This is typically resolved by:

1.) You may try to remove the -lz or -lgz flag from the libs list
    by using the --libs switch for "perl Makefile.PL".
2.) On Red Hat Linux install libz-devel
3.) On other systems, please contact the mailing list

     [email]Msql-Mysql-modules@lists.mysql.com[/email]

For further hints, see INSTALL.html, section Linker flags.
make: *** [blib/arch/auto/DBD/mysql/mysql.so] Error 1
  /usr/bin/make  -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Failed during this command:
  CAPTTOFU/DBD-mysql-3.0002.tar.gz             : make NO

---

