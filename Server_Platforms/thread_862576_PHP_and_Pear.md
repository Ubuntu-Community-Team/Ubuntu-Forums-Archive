---
title: "PHP and Pear"
date: 2008-07-17
forum: Server Platforms
---

### Post by matthewboh on 2008-07-17
I'm having a really strange problem - PHP can't resolve a call to DB - here's the error message
```
Fatal error: Class 'DB' not found in /var/www/timetracker/WEB-INF/clib/User.class.php on line 94
```, but when I do 

```
 pear list
Installed packages, channel pear.php.net:
=========================================
Package            Version State
Archive_Tar        1.3.2   stable
Console_Getopt     1.2.3   stable
DB                 1.7.13  stable
Date               1.4.7   stable
Fileinfo           1.0.4   stable
HTTP_Request       1.4.2   stable
MDB2               2.4.1   stable
MDB2_Driver_mysql  1.4.1   stable
MDB2_Driver_mysqli 1.4.1   stable
Net_URL            1.0.15  stable
PEAR               1.6.1   stable
SOAP               0.11.0  beta
Structures_Graph   1.0.2   stable
``` it shows that DB is there.  Am I missing something?

---

