---
title: "Problems compiling PHP with IMAP"
date: 2011-04-21
forum: Server Platforms
---

### Post by SHREDDER007 on 2011-04-21
Hi everyone. I'm setting up an Ubuntu 10.10 server at work and I'm having an issue when compiling PHP, and I think it has something to do with my IMAP configuration.

I run my configure command just fine:
```
sudo ./configure --prefix=/usr/local/php --libdir=/usr/local/php/lib --includedir=/usr/local/php/include --with-config-file-path=/etc --with-config-file-scan-dir=/etc/php.d --enable-libgcc --disable-short-tags --with-libxml-dir=/usr/lib --with-openssl=/usr/local/ssl --with-zlib --enable-bcmath --enable-calendar --with-curl --enable-ftp --with-gd --enable-gd-native-ttf --enable-gd-jis-conv --with-freetype-dir=/usr/local/lib --with-jpeg-dir=/usr/local/lib --with-t1lib --with-imap=/usr/local/imap --with-imap-ssl=/usr/local/ssl --enable-mbstring --with-mcrypt --with-mhash --with-mysql=/usr/local/mysql --with-mysql-sock=/var/tmp/mysql.sock --with-mysqli=/usr/local/mysql/bin/mysql_config --with-zlib-dir=/usr/lib --with-pspell=/usr --enable-soap --enable-wddx --enable-zip --with-pear --enable-zend-multibyte --with-apxs2=/usr/local/apache2/bin/apxs --with-pdo-mysql=/usr/local/mysql --with-kerberos --with-openssl-dir=/usr/local/ssl/ --enable-static=openssl
```


Then when I go to run my "sudo make", it errors out with this:
```
/usr/bin/ld: /usr/local/imap/lib/libc-client.a(osdep.o): relocation R_X86_64_32 against `server_input_wait' can not be used when making a shared object; recompile with -fPIC
/usr/local/imap/lib/libc-client.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [libphp5.la] Error 1

```

I've been looking all over the internet and have yet to find a working solution, so any suggestions/input would be greatly appreciated. Thanks!

---

