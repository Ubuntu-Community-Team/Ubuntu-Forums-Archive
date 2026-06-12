---
title: "PDO postgresql driver"
date: 2011-04-26
forum: Server Platforms
---

### Post by karq on 2011-04-26
Hey!

maybe someone can help, I'm trying to install PDO pgsql driver with pecl

When I run 
```
sudo pecl install pdo_pgsql
```

Then I get this error:
```
configure: error: Cannot find php_pdo_driver.h.
ERROR: `/tmp/pear/temp/PDO_PGSQL/configure' failed

```

---

### Post by dtfinch on 2011-04-26
You might need to install php5-dev (apt-get) first.

---

### Post by karq on 2011-04-26
Php5-dev is installed.the problem is not there

---

### Post by dtfinch on 2011-04-27
If you install [php5-pgsql](https://launchpad.net/ubuntu/lucid/+package/php5-pgsql), that's supposed to include pdo_pgsql.

The page for the [PECL PDO extension](http://pecl.php.net/package/PDO) says not to use the PECL version anymore, as PDO is now part of the core of php.

---

### Post by karq on 2011-04-27
Thanks, that did the trick.

---

