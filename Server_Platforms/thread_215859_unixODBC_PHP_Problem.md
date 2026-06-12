---
title: "unixODBC PHP Problem"
date: 2006-07-14
forum: Server Platforms
---

### Post by michaela on 2006-07-14
I am using Ubuntu 6.06. I have unixODBC installed as well as FreeTDS. I am using PHP 5.1.4.

I have read several How-Tos and am stuck on a problem.

I tested FreeTDS by using tsql and it works.

I tested unixODBC by using isql and it works.

When I created a script in PHP and tried to access a database I get the following errors.



Warning: odbc_connect() [function.odbc-connect]: SQL error: [unixODBC][Driver Manager]Data source name not found, and no default driver specified, SQL state IM002 in SQLConnect in /var/www/htdocs/test.php on line 2

Warning: odbc_exec(): supplied argument is not a valid ODBC-Link resource in /var/www/htdocs/test.php on line 4

Warning: odbc_fetch_row(): supplied argument is not a valid ODBC result resource in /var/www/htdocs/test.php on line 5

Warning: odbc_close(): supplied argument is not a valid ODBC-Link resource in /var/www/htdocs/test.php on line 10



It is acting like PHP cannot find the DSN. I have found multiple php.ini files. Which is the one that Ubuntu 6.06 Apache2 uses? Is there something in there that needs to be set. The lines for ODBC I saw in php.ini say that they are not working yet.

Is there some setting that I missed seting that was not in the How-Tos?

All help is greatly appreciated.

TIA.

Mike

---

### Post by solowookie on 2007-08-20
I am considering using UnixODBC did you ever get this resolved?

:popcorn:

---

