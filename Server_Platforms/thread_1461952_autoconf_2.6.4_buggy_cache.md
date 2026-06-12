---
title: "autoconf 2.6.4 buggy cache"
date: 2010-04-24
forum: Server Platforms
---

### Post by TDK800 on 2010-04-24
Edit: solution is installing older version = "aptitude install autoconf2.13"

sudo aptitude install autoconf
* then rebuilding php 5.3.2 configure script:
rm configure
./buildconf --force

* result:
Forcing buildconf
buildconf: checking installation...
buildconf: autoconf version 2.64 (ok)
buildconf: Your version of autoconf likely contains buggy cache code.
           Running vcsclean for you.
           To avoid this, install autoconf-2.13.
Can't figure out your VCS, not cleaning.
rebuilding configure
ext/pdo_dblib/config.m4:56: warning: AC_CACHE_VAL(pdo_inc_path, ...): suspicious cache-id, must contain _cv_ to be cached
../../lib/autoconf/general.m4:2018: AC_CACHE_VAL is expanded from...
../../lib/autoconf/general.m4:2039: AC_CACHE_CHECK is expanded from...
aclocal.m4:2738: PHP_CHECK_PDO_INCLUDES is expanded from...
ext/pdo_firebird/config.m4:48: warning: AC_CACHE_VAL(pdo_inc_path, ...): suspicious cache-id, must contain _cv_ to be cached
ext/pdo_mysql/config.m4:138: warning: AC_CACHE_VAL(pdo_inc_path, ...): suspicious cache-id, must contain _cv_ to be cached
ext/pdo_oci/config.m4:196: warning: AC_CACHE_VAL(pdo_inc_path, ...): suspicious cache-id, must contain _cv_ to be cached
ext/pdo_odbc/config.m4:44: warning: AC_CACHE_VAL(pdo_inc_path, ...): suspicious cache-id, must contain _cv_ to be cached
ext/pdo_pgsql/config.m4:106: warning: AC_CACHE_VAL(pdo_inc_path, ...): suspicious cache-id, must contain _cv_ to be cached
ext/pdo_sqlite/config.m4:16: warning: AC_CACHE_VAL(pdo_inc_path, ...): suspicious cache-id, must contain _cv_ to be cached
ext/sqlite/config.m4:50: warning: AC_CACHE_VAL(pdo_inc_path, ...): suspicious cache-id, must contain _cv_ to be cached
rebuilding main/php_config.h.in
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows one to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader: 		[Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
ext/pdo_dblib/config.m4:56: warning: AC_CACHE_VAL(pdo_inc_path, ...): suspicious cache-id, must contain _cv_ to be cached
../../lib/autoconf/general.m4:2018: AC_CACHE_VAL is expanded from...
../../lib/autoconf/general.m4:2039: AC_CACHE_CHECK is expanded from...
aclocal.m4:2738: PHP_CHECK_PDO_INCLUDES is expanded from...
ext/pdo_firebird/config.m4:48: warning: AC_CACHE_VAL(pdo_inc_path, ...): suspicious cache-id, must contain _cv_ to be cached
ext/pdo_mysql/config.m4:138: warning: AC_CACHE_VAL(pdo_inc_path, ...): suspicious cache-id, must contain _cv_ to be cached
ext/pdo_oci/config.m4:196: warning: AC_CACHE_VAL(pdo_inc_path, ...): suspicious cache-id, must contain _cv_ to be cached
ext/pdo_odbc/config.m4:44: warning: AC_CACHE_VAL(pdo_inc_path, ...): suspicious cache-id, must contain _cv_ to be cached
ext/pdo_pgsql/config.m4:106: warning: AC_CACHE_VAL(pdo_inc_path, ...): suspicious cache-id, must contain _cv_ to be cached
ext/pdo_sqlite/config.m4:16: warning: AC_CACHE_VAL(pdo_inc_path, ...): suspicious cache-id, must contain _cv_ to be cached
ext/sqlite/config.m4:50: warning: AC_CACHE_VAL(pdo_inc_path, ...): suspicious cache-id, must contain _cv_ to be cached

---

### Post by windependence on 2010-04-24
Why not just install the package?

-Tim

---

