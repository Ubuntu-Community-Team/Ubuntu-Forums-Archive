---
title: "compile php5 with bundled gd"
date: 2013-06-02
forum: Server Platforms
---

### Post by zenmatrix on 2013-06-02
I need the imageantialias() to work on the server I built. I have complied PHP before but for some reason I can't do it any more. I ran these steps to try:
1.apt-get source php5
2.apt-get build-dep php5
3.cd php5-*
4.nano debian/rules
5.find this line --with-gd=shared,/usr --enable-gd-native-ttf \ and remove ,/usr
6.save and exit
7.nano debian/setup_mysql.sh
8.search for Start the daemon
9.add –user=root after the mysqld
10.save and exit
11.dpkg-buildpackage –rfakeroot -us –uc -d

then it runs for a long time and then it ends here:
make[1]: Leaving directory `/usr/src/php5-5.3.10/cgi-build'
    sed -i -e 's/-d output_buffering=1 -d open_basedir="" -d safe_mode=0/-d output_buffering=1 -d open_basedir="" -d safe_mode=0 -d memory_limit="-1"/' \
           /usr/src/php5-5.3.10/pear-build/usr/bin/pear && \
    sed -i -e 's/-d output_buffering=1 -d safe_mode=0/-d output_buffering=1 -d open_basedir="" -d safe_mode=0 -d memory_limit="-1"/' \
           /usr/src/php5-5.3.10/pear-build/usr/bin/pecl && \
    sed -i -e 's/-d memory_limit="-1"//' \
           -e 's/-d output_buffering=1 -d open_basedir="" -d safe_mode=0/-d output_buffering=1 -d open_basedir="" -d safe_mode=0 -d memory_limit="-1"/' \
           /usr/src/php5-5.3.10/pear-build/usr/bin/peardev
    sed -i -re "s#('PEAR_CONFIG_SYSCONFDIR', PHP_SYSCONFDIR)#\1 . '/pear'#" /usr/src/php5-5.3.10/pear-build/usr/share/php/PEAR/Config.php
    patch -s -d /usr/src/php5-5.3.10/pear-build/usr/share/php/ -p1 -i /usr/src/php5-5.3.10/debian/patches/PEAR-Builder-print-info-about-php5-dev.patch
    touch build-pear-stamp
    mkdir -p temp_session_store
    # start our own mysql server for the tests
    /bin/sh debian/setup-mysql.sh 2963 /usr/src/php5-5.3.10/mysql_db
make: *** [test-results.txt] Error 1
    dpkg-buildpackage: error: debian/rules build gave error exit status 2


I tried it without modifying the setup-mysql.sh as well but the same thing happens. I'm not really sure why this isn't working. I know the last time I did this I had a lot of trouble. Also I've tried this on two separate 12.04 servers with the same problem

---

### Post by SeijiSensei on 2013-06-02
Have you tried installing the standard PHP package and adding the **php5-gd** package to include the gd libraries?

---

### Post by zenmatrix on 2013-06-02
they don't contain the imageantialias function, which I find irritating. The php5-gd package is really behind the times from what I've read and needs to be updated.

---

### Post by mmerlone on 2014-03-25
> **zenmatrix said:**
> I need the imageantialias() to work on the server I built. I have complied PHP before but for some reason I can't do it any more. I ran these steps to try:
(...)
then it runs for a long time and then it ends here:
make[1]: Leaving directory `/usr/src/php5-5.3.10/cgi-build'
(...)
    # start our own mysql server for the tests
    /bin/sh debian/setup-mysql.sh 2963 /usr/src/php5-5.3.10/mysql_db
make: *** [test-results.txt] Error 1
    dpkg-buildpackage: error: debian/rules build gave error exit status 2
I tried it without modifying the setup-mysql.sh as well but the same thing happens. I'm not really sure why this isn't working. I know the last time I did this I had a lot of trouble. Also I've tried this on two separate 12.04 servers with the same problem

Hi, have you found a solution or workaround? I am running on the exactly same need and issue.

---

