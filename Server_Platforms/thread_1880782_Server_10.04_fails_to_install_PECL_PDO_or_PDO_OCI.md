---
title: "Server 10.04 fails to install PECL PDO or PDO_OCI"
date: 2011-11-14
forum: Server Platforms
---

### Post by igorsantos07 on 2011-11-14
I'm trying to install PDO_OCI in my Ubuntu 10.04.1 server but it fails.
I've installed php5-dev via apt-get, and when I try to run "pecl install pdo_oci" it asks for the pdo package; if I try "pecl install pdo" it throws me this:

> 
/tmp/pear/temp/PDO/pdo_dbh.c: In function ‘pdo_stmt_instantiate’:
/tmp/pear/temp/PDO/pdo_dbh.c:410:8: error: ‘zval’ has no member named ‘refcount’
/tmp/pear/temp/PDO/pdo_dbh.c:411:8: error: ‘zval’ has no member named ‘is_ref’
/tmp/pear/temp/PDO/pdo_dbh.c: In function ‘pdo_stmt_construct’:
/tmp/pear/temp/PDO/pdo_dbh.c:435:6: error: ‘zend_fcall_info’ has no member named ‘object_pp’
/tmp/pear/temp/PDO/pdo_dbh.c:458:6: error: ‘zend_fcall_info_cache’ has no member named ‘object_pp’
/tmp/pear/temp/PDO/pdo_dbh.c: In function ‘zim_PDO_setAttribute’:
/tmp/pear/temp/PDO/pdo_dbh.c:752:12: error: ‘zval’ has no member named ‘refcount’
/tmp/pear/temp/PDO/pdo_dbh.c: In function ‘zim_PDO_getAttribute’:
/tmp/pear/temp/PDO/pdo_dbh.c:818:28: error: ‘zval’ has no member named ‘refcount’
/tmp/pear/temp/PDO/pdo_dbh.c: In function ‘pdo_hash_methods’:
/tmp/pear/temp/PDO/pdo_dbh.c:1122:24: warning: assignment discards qualifiers from pointer target type
/tmp/pear/temp/PDO/pdo_dbh.c:1126:20: warning: assignment discards qualifiers from pointer target type
make: *** [pdo_dbh.lo] Error 1
ERROR: `make' failed


How can I install it? The default OCI extension for PHP is not useful for me, only the PDO_OCI.

---

