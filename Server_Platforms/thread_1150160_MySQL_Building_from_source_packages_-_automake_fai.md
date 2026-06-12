---
title: "MySQL: Building from source packages - automake fails"
date: 2009-05-05
forum: Server Platforms
---

### Post by geekylucas on 2009-05-05
Hi,

I am having problems building from the MySQL source packages.  Here are the commands I am running and the output I am seeing.  Is it reasonable to expect that automake will work here?

Using Ubuntu 8.04.

```
apt-get source mysql-server
cd mysql-dfsg-5.0-5.0.51a
sh BUILD/autorun.sh
```
```
/usr/share/aclocal/libmcrypt.m4:17: warning: underquoted definition of AM_PATH_LIBMCRYPT
/usr/share/aclocal/libmcrypt.m4:17:   run info '(automake)Extending aclocal'
/usr/share/aclocal/libmcrypt.m4:17:   or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
BUILD/Makefile.am:70: `%'-style pattern rules are a GNU make extension
SSL/Makefile.am:21: `%'-style pattern rules are a GNU make extension
client/Makefile.am:77: `%'-style pattern rules are a GNU make extension
cmd-line-utils/Makefile.am:24: `%'-style pattern rules are a GNU make extension
cmd-line-utils/libedit/Makefile.am:100: `%'-style pattern rules are a GNU make extension
cmd-line-utils/readline/Makefile.am:37: `%'-style pattern rules are a GNU make extension
dbug/Makefile.am:65: `%'-style pattern rules are a GNU make extension
extra/Makefile.am:53: `%'-style pattern rules are a GNU make extension
extra/yassl/Makefile.am:5: `%'-style pattern rules are a GNU make extension
extra/yassl/src/Makefile.am:7: wildcard ../include/*.hpp: non-POSIX variable name
extra/yassl/src/Makefile.am:7: (probably a GNU make extension)
extra/yassl/src/Makefile.am:7: wildcard ../include/openssl/*.h: non-POSIX variable name
extra/yassl/src/Makefile.am:7: (probably a GNU make extension)
extra/yassl/src/Makefile.am:11: `%'-style pattern rules are a GNU make extension
extra/yassl/taocrypt/Makefile.am:2: wildcard mySTL/*.hpp: non-POSIX variable name
extra/yassl/taocrypt/Makefile.am:2: (probably a GNU make extension)
extra/yassl/taocrypt/Makefile.am:5: `%'-style pattern rules are a GNU make extension
extra/yassl/taocrypt/benchmark/Makefile.am:9: `%'-style pattern rules are a GNU make extension
extra/yassl/taocrypt/src/Makefile.am:13: wildcard ../include/*.hpp: non-POSIX variable name
extra/yassl/taocrypt/src/Makefile.am:13: (probably a GNU make extension)
extra/yassl/taocrypt/src/Makefile.am:16: `%'-style pattern rules are a GNU make extension
extra/yassl/taocrypt/test/Makefile.am:9: `%'-style pattern rules are a GNU make extension
extra/yassl/testsuite/Makefile.am:13: `%'-style pattern rules are a GNU make extension
heap/Makefile.am:32: `%'-style pattern rules are a GNU make extension
include/Makefile.am:78: `%'-style pattern rules are a GNU make extension
libmysql/Makefile.shared:117: `%'-style pattern rules are a GNU make extension
libmysql/Makefile.am:29:   `libmysql/Makefile.shared' included from here
libmysql/Makefile.am:116: `%'-style pattern rules are a GNU make extension
libmysql/Makefile.shared:117: `%'-style pattern rules are a GNU make extension
libmysql_r/Makefile.am:30:   `libmysql/Makefile.shared' included from here
libmysql_r/Makefile.am:47: `%'-style pattern rules are a GNU make extension
libmysqld/Makefile.am:160: `%'-style pattern rules are a GNU make extension
libmysqld/examples/Makefile.am:53: `%'-style pattern rules are a GNU make extension
man/Makefile.am:25: `%'-style pattern rules are a GNU make extension
myisam/Makefile.am:107: `%'-style pattern rules are a GNU make extension
myisammrg/Makefile.am:27: `%'-style pattern rules are a GNU make extension
mysql-test/Makefile.am:153: `%'-style pattern rules are a GNU make extension
mysql-test/ndb/Makefile.am:24: `%'-style pattern rules are a GNU make extension
mysys/Makefile.am:127: `%'-style pattern rules are a GNU make extension
ndb/Makefile.am:49: `%'-style pattern rules are a GNU make extension
ndb/docs/Makefile.am:132: `%'-style pattern rules are a GNU make extension
ndb/include/Makefile.am:65: `%'-style pattern rules are a GNU make extension
ndb/src/Makefile.am:53: `%'-style pattern rules are a GNU make extension
ndb/src/common/Makefile.am:33: `%'-style pattern rules are a GNU make extension
ndb/src/common/debugger/Makefile.am:26: `%'-style pattern rules are a GNU make extension
ndb/src/common/debugger/signaldata/Makefile.am:47: `%'-style pattern rules are a GNU make extension
ndb/src/common/logger/Makefile.am:26: `%'-style pattern rules are a GNU make extension
ndb/src/common/mgmcommon/Makefile.am:29: `%'-style pattern rules are a GNU make extension
ndb/src/common/portlib/Makefile.am:59: `%'-style pattern rules are a GNU make extension
ndb/src/common/transporter/Makefile.am:36: `%'-style pattern rules are a GNU make extension
ndb/src/common/util/Makefile.am:49: `%'-style pattern rules are a GNU make extension
ndb/src/cw/Makefile.am:21: `%'-style pattern rules are a GNU make extension
ndb/src/cw/cpcd/Makefile.am:32: `%'-style pattern rules are a GNU make extension
ndb/src/kernel/Makefile.am:74: `%'-style pattern rules are a GNU make extension
ndb/src/kernel/blocks/Makefile.am:36: `%'-style pattern rules are a GNU make extension
ndb/src/kernel/blocks/backup/Makefile.am:24: `%'-style pattern rules are a GNU make extension
ndb/src/kernel/blocks/cmvmi/Makefile.am:24: `%'-style pattern rules are a GNU make extension
ndb/src/kernel/blocks/dbacc/Makefile.am:26: `%'-style pattern rules are a GNU make extension
ndb/src/kernel/blocks/dbdict/Makefile.am:34: `%'-style pattern rules are a GNU make extension
ndb/src/kernel/blocks/dbdih/Makefile.am:30: `%'-style pattern rules are a GNU make extension
ndb/src/kernel/blocks/dblqh/Makefile.am:30: `%'-style pattern rules are a GNU make extension
ndb/src/kernel/blocks/dbtc/Makefile.am:24: `%'-style pattern rules are a GNU make extension
ndb/src/kernel/blocks/dbtup/Makefile.am:43: `%'-style pattern rules are a GNU make extension
ndb/src/kernel/blocks/dbtux/Makefile.am:35: `%'-style pattern rules are a GNU make extension
ndb/src/kernel/blocks/dbutil/Makefile.am:24: `%'-style pattern rules are a GNU make extension
ndb/src/kernel/blocks/ndbcntr/Makefile.am:27: `%'-style pattern rules are a GNU make extension
ndb/src/kernel/blocks/ndbfs/Makefile.am:28: `%'-style pattern rules are a GNU make extension
ndb/src/kernel/blocks/qmgr/Makefile.am:26: `%'-style pattern rules are a GNU make extension
ndb/src/kernel/blocks/suma/Makefile.am:24: `%'-style pattern rules are a GNU make extension
ndb/src/kernel/blocks/trix/Makefile.am:24: `%'-style pattern rules are a GNU make extension
ndb/src/kernel/error/Makefile.am:26: `%'-style pattern rules are a GNU make extension
ndb/src/kernel/vm/Makefile.am:44: `%'-style pattern rules are a GNU make extension
ndb/src/mgmapi/Makefile.am:30: `%'-style pattern rules are a GNU make extension
ndb/src/mgmclient/Makefile.am:48: `%'-style pattern rules are a GNU make extension
ndb/src/mgmsrv/Makefile.am:61: `%'-style pattern rules are a GNU make extension
ndb/src/ndbapi/Makefile.am:63: `%'-style pattern rules are a GNU make extension
ndb/test/Makefile.am:26: `%'-style pattern rules are a GNU make extension
ndb/test/ndbapi/Makefile.am:119: `%'-style pattern rules are a GNU make extension
ndb/test/ndbapi/bank/Makefile.am:36: `%'-style pattern rules are a GNU make extension
ndb/test/run-test/Makefile.am:45: `%'-style pattern rules are a GNU make extension
ndb/test/src/Makefile.am:35: `%'-style pattern rules are a GNU make extension
ndb/test/tools/Makefile.am:42: `%'-style pattern rules are a GNU make extension
ndb/tools/Makefile.am:80: `%'-style pattern rules are a GNU make extension
netware/Makefile.am:117: `%'-style pattern rules are a GNU make extension
os2/Makefile.am:27: `%'-style pattern rules are a GNU make extension
os2/include/Makefile.am:22: `%'-style pattern rules are a GNU make extension
os2/include/sys/Makefile.am:21: `%'-style pattern rules are a GNU make extension
pstack/Makefile.am:35: `%'-style pattern rules are a GNU make extension
pstack/aout/Makefile.am:4: `%'-style pattern rules are a GNU make extension
regex/Makefile.am:36: `%'-style pattern rules are a GNU make extension
scripts/Makefile.am:190: `%'-style pattern rules are a GNU make extension
server-tools/Makefile.am:20: `%'-style pattern rules are a GNU make extension
server-tools/instance-manager/Makefile.am:94: `%'-style pattern rules are a GNU make extension
sql-bench/Makefile.am:86: `%'-style pattern rules are a GNU make extension
sql-common/Makefile.am:20: `%'-style pattern rules are a GNU make extension
sql/Makefile.am:179: `%'-style pattern rules are a GNU make extension
configure.in: installing `./ylwrap'
sql/share/Makefile.am:62: `%'-style pattern rules are a GNU make extension
strings/Makefile.am:79: `%'-style pattern rules are a GNU make extension
support-files/MacOSX/Makefile.am:57: `%'-style pattern rules are a GNU make extension
support-files/Makefile.am:115: `%'-style pattern rules are a GNU make extension
support-files/RHEL4-SElinux/Makefile.am:23: `%'-style pattern rules are a GNU make extension
tests/Makefile.am:58: `%'-style pattern rules are a GNU make extension
tools/Makefile.am:30: `%'-style pattern rules are a GNU make extension
vio/Makefile.am:28: `%'-style pattern rules are a GNU make extension
win/Makefile.am:21: `%'-style pattern rules are a GNU make extension
zlib/Makefile.am:38: `%'-style pattern rules are a GNU make extension
configure.in:2981: required file `Docs/Makefile.in' not found
configure.in:2981: required file `debian/Makefile.in' not found
configure.in:2981: required file `debian/defs.mk.in' not found
configure.in:2981: required file `debian/control.in' not found
Can't execute automake
```

Running automake.sh on the source tarball downloaded from mysql.com works just fine.

Also note that if I run dpkg-buildpackage on an unaltered source package the build works fine.

The reason I need to run automake.sh is because I am applying a patch (sphinxse) to the mysql source which requires this script to be run. I have tried running it with & without the patch with the same results.

---

### Post by windependence on 2009-05-06
Any particular reason you won't use a package? If you really want to compile everything for whatever reason, FreeBSD is where you want to be.

-Tim

---

### Post by geekylucas on 2009-05-06
I would love to use a package but unfortunately none exist for MySQL with Sphinx Storage Engine enabled.

This is why I'm trying to create a package as per the original post. :)

---

### Post by windependence on 2009-05-07
That's wierd, in FreeBSD it's a separate package that connects to an SQL database. This is what it says in the FreeBSD ports collection:

> **Port description for textproc/sphinxsearch**

   Sphinx is a full-text search engine, distributed under GPL version
2. Commercial license is also available for embedded use.

Generally, it's a standalone search engine, meant to provide fast,
size-efficient and relevant fulltext search functions to other
applications. Sphinx was specially designed to integrate well with SQL
databases and scripting languages. Currently built-in data sources
support fetching data either via direct connection to MySQL, or from
an XML pipe.

As for the name, Sphinx is an acronym which is officially decoded as
SQL Phrase Index.

WWW: [http://www.sphinxsearch.com/](http://www.sphinxsearch.com/)


That would tend to make me believe it should be written as a single package for Linux as well but of course there is no guarantee. Are you doing this on a web site? If so, do you HAVE to host it on Linux? I use FreeBSD on all my web sites because I think it's more stable, more secure, and has a smaller footprint than Linux. I also tend to think the file system is much cleaner and simpler. Of course YMMV, but if you want to consider it, I will help you.

-Tim

---

### Post by cyrano24100 on 2009-09-26
windependence: Your response is close to insulting;

----

I have the same problem as above.

I'm trying to build mysql/Sphinx on Ubuntu 8.04 -- getting the same problem as geekylucas.

I have been able to do this in the past using mysql-source from:
[https://launchpad.net/ubuntu/hardy/+source/mysql-dfsg-5.0/](https://launchpad.net/ubuntu/hardy/+source/mysql-dfsg-5.0/)
But that was mysql-dfsg-5.0 5.0.51a-3ubuntu5.1
Now the package is mysql-dfsg-5.0 5.0.51a-3ubuntu5.4
and that mysql does not "dpkg-buildpackage" or "automake" correctly and gives the same errors as above:

configure.in:2981: required file `Docs/Makefile.in' not found
configure.in:2981: required file `debian/Makefile.in' not found
configure.in:2981: required file `debian/defs.mk.in' not found
configure.in:2981: required file `debian/control.in' not found


Anyone has a fix?


(and no, windependence I don't want to use FreeBSD, I DO like FreeBSD, and use it for some other customers... I just can't believe you get "Tall Cafè Ubuntu" by putting vague FreeBSD propaganda on an ubuntu forum though.)




.

---

