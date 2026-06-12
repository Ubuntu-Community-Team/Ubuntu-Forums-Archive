---
title: "php and ms-sql on 11.04"
date: 2011-07-17
forum: Server Platforms
---

### Post by mod_plod on 2011-07-17
hi all.

I am trying to set up my 11.04 ubuntu install so that php can access ms-sql servers. I have done this twice before once with ver 9.10 and centos 5. So I figure I would follow the same steps again as I did last time. but its not working this time around

I get to building php and get the following error.  I do not often build packages as I dont know much about it so I figure I have missed something some place. Can anyone tell me what this means and a clue to where I can find the fix. Thanks


>> dpkg-buildpackage
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package php5
dpkg-buildpackage: source version 5.3.5-1ubuntu7.2
dpkg-buildpackage: source changed by Steve Beattie <sbeattie@ubuntu.com>
dpkg-buildpackage: host architecture i386
 dpkg-source --before-build php5-5.3.5
 debian/rules clean
dh_testdir
sed -i -e 's/EXTRA_VERSION="-1ubuntu7.2"/EXTRA_VERSION=""/' configure.in
rm -f prepared-stamp
QUILT_PATCHES=debian/patches \
		quilt --quiltrc /dev/null pop -a -R || test $? = 2
Patch fix_crash_in__php_mssql_get_column_content_without_type.patch does not remove cleanly (refresh it or enforce with -f)
make: *** [unpatch] Error 1
dpkg-buildpackage: error: debian/rules clean gave error exit status 2
root@server2:/home/leigh/php5-5.3.5# dpkg-buildpackage
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package php5
dpkg-buildpackage: source version 5.3.5-1ubuntu7.2
dpkg-buildpackage: source changed by Steve Beattie <sbeattie@ubuntu.com>
dpkg-buildpackage: host architecture i386
 dpkg-source --before-build php5-5.3.5
 debian/rules clean
dh_testdir
sed -i -e 's/EXTRA_VERSION="-1ubuntu7.2"/EXTRA_VERSION=""/' configure.in
rm -f prepared-stamp
QUILT_PATCHES=debian/patches \
		quilt --quiltrc /dev/null pop -a -R || test $? = 2
Patch fix_crash_in__php_mssql_get_column_content_without_type.patch does not remove cleanly (refresh it or enforce with -f)
make: *** [unpatch] Error 1
dpkg-buildpackage: error: debian/rules clean gave error exit status 2

---

### Post by SeijiSensei on 2011-07-18
Let's start from scratch.  Why are you building PHP from source rather than installing the copy that's in the repositories?  

If you install the stock PHP and the **php5-sybase** module, you'll get MS SQL functions.  Alternatively you can install **php-odbc** and use ODBC instead.  You can install both modules and try them both.

---

