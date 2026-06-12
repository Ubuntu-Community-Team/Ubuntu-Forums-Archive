---
title: "mssql_connect not recognysed with PHP"
date: 2005-06-20
forum: Server Platforms
---

### Post by nverhaar on 2005-06-20
We have an Ubuntu server running Apache2 and PHP4, and are attempting to get it talking with a Sybase database server. We have installed FreeTDS and are able to succesfully connect to the server, however the MSSQL functions within PHP are not recognysed, (ie, mssql_connect).

Is there an easy way to implement support for these functions via apt-get, or do we need to compile PHP from scratch with support for these functions?

PLEASE HELP!!!

 ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by nverhaar on 2005-06-23
Nevermind, I figured this one out myself eventually!!

After installing the php4-sybase package, the mssql functions came to life!

 :grin:  :grin:  :grin:  :grin:

---

### Post by panthar on 2006-06-16
I also have a MSSQL database I need to connect to with PHP - the sybase module did enable the mssql_connect function, but I got bad results when trying to do queries, etc.  I had much better luck when I rebuilt PHP with real mssql support - I documented the process at: [http://panthar.org/2006/06/15/php-with-mssql-on-ubuntu-606/](http://panthar.org/2006/06/15/php-with-mssql-on-ubuntu-606/)

---

### Post by Parama on 2006-10-30
Thank you so much, panthar, for that neat guide! That really just did it. 5 of 5 stars would be my rating. I had no idea it was that easy to rebuild PHP.

---

