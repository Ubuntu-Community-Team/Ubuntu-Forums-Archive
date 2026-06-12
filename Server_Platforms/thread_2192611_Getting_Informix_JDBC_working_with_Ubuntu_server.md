---
title: "Getting Informix JDBC working with Ubuntu server"
date: 2013-12-08
forum: Server Platforms
---

### Post by themacboy on 2013-12-08
Guys,

I have an ubuntu server setup that I want to do some PHP work on. I need this server to talk to an informix database.

Should I get that connection going via ODBC or use the PDO_INFORMIX pecl package?

Either way I am stuggling to get one of them working.

For the PDO package I cant seem to install the informix package ([http://pecl.php.net/package/PDO_INFORMIX](http://pecl.php.net/package/PDO_INFORMIX)) I get this error

> sudo pecl install PDO_INFORMIX
 
> pecl.php.net is using a unsupported protocol - This should never happen.
pecl/PDO_INFORMIX requires package "pear/PDO"
No valid packages found
install failed

Now since PHP version 5.3 PDO is installed and enabled by default, so I know I dont need to install PDO. I have the PDO_INFORMIX code downloaded and on my system, but I have no idea how to (or if I should) build it.

For ODBC, I have installed the Informix Client SDK, and the UnixODBC code. I have setup my odbc.ini (in /etc) but I still cant get it to connect.

Everytime I try and connect I get this error:

> isql db_cra

> [ISQL]ERROR: Could not SQLConnect

Ideas?

Cheers

---

