---
title: "Trouble installing PHP"
date: 2005-12-19
forum: Server Platforms
---

### Post by badgerbox76 on 2005-12-19
I am trying to install php 5.1.1 on my Ubuntu box and i am going through the steps as posted here [http://www.ubuntuforums.org/showthread.php?t=98215](http://www.ubuntuforums.org/showthread.php?t=98215) but i am runing in to errors and here is what i am geting


nos@ubuntu:~/php-5.1.1$ ./configure --prefix=/usr/local/apache2/php --with-config-file-path=/usr/local/apache2/php --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql --enable-gd --with-gd --with-xsl --enable-xslt --with-xslt-sablot --with-xml --with-zlib --enable-calendar --enable-sysvsem --enable-sysvshm --enable-sysvmsg --enable-track-vars --enable-trans-sid --enable-bcmath --with-bz2 --enable-ctype --with-db4 --with-regex=php
loading cache ./config.cache
checking for Cygwin environment... no
checking for mingw32 environment... no
checking for egrep... grep -E
checking for a sed that does not truncate output... /bin/sed
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for AIX... no
checking whether ln -s works... yes
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking for re2c... no
configure: warning: You will need re2c 0.98 or later if you want to regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for bison... no
checking for byacc... no
checking for bison version... invalid
configure: warning: bison versions supported for regeneration of the Zend/PHP parsers: 1.28 1.35 1.75 1.875 2.0 2.1 (found: none).
checking for flex... lex
checking for yywrap in -ll... no
checking lex output file root... ./configure: line 3238: lex: command not found
configure: error: cannot find output from lex; giving up
nos@ubuntu:~/php-5.1.1$

---

### Post by tameritoke on 2005-12-20
So easy to solve it! I had it before too!
download with the ADEPT tool the latest flex version (if there are development libraries to download, do it either to be sure!) Then run configure again! 

make 
sudo make install

Here is my PHP configure script:

'./configure' '--with-apxs2=/usr/local/apache2/bin/apxs' '--enable-calendar' '--with-zlib=shared' '--with-openssl=shared' '--with-mysql=shared,/opt/mysql-50' '--enable-mbstring' '--with-mcrypt=shared' '--with-pdo-mysql=shared,/opt/mysql-50' '--with-gd=shared'


for mysql:
'--with-mysql=shared,/opt/mysql-50' 
'--with-pdo-mysql=shared,/opt/mysql-50'

You need to modify the path where your version is being installed to!

Extra info!
If you really want that stuff run fast as suggar add your compiler flaggs (but before install the suitable kernel with ith's headers for your CPU!!!) export settings in /etc/bash.bashrc, then it's system wide!



Tamer

---

### Post by badgerbox76 on 2005-12-21
Thanks much it worked!!!!

---

