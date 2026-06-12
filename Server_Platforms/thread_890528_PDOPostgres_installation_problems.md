---
title: "PDO/Postgres installation problems"
date: 2008-08-15
forum: Server Platforms
---

### Post by Mickeysofine1972 on 2008-08-15
As Ubuntu is a debian based system I though I might as well post here to ask for help.

My problem is this:

I have a debian etch server that uses apache2, mysql and Postgres to server websites.

I have been abl eto do an upgrade lateley fo rthe apache2 software but have found that any of the sites on there that use use postgress are now not working.

I get the following error in the apache2 log:
```

PHP Fatal error:  PDO: driver odbc requires PDO API version 20060511; this is PDO version 20060409 in Unknown on line 0
PHP Fatal error:  Unable to start PDO_ODBC module in Unknown on line 0

```i used pecl to install the PDO and PDO_PGSQL and found that apache2 wont start when they are installed becuase of the modules not matching versions.

How can I fix this and get my server back up and running?

Thanks in advance !

Mike

---

### Post by gr8whitesavage on 2008-11-14
Did you resolve this issue? If so, how did you do it?

I'm having a similar problem.

---

### Post by Mickeysofine1972 on 2008-11-14
Hi

Yes I did fix this but only by downloading the source and changing the version number in the source then compiling and installing the .so file it generates into the locations that php looks for the the module. thats set in your php.ini inside the /etc/php5/apache folder on debian systems

hope that helps

Mike

---

