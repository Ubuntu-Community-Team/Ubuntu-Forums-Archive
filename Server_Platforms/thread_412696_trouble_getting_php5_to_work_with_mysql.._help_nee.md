---
title: "trouble getting php5 to work with mysql.. help needed"
date: 2007-04-18
forum: Server Platforms
---

### Post by cyrano_says on 2007-04-18
i have been working on perl so far..
wanted to give php5 a shot..

i got mysql and apache2 and php working..

but when i try to use mysql_connect() in a php script..

it gives me an error

"Fatal error: Call to undefined function mysql_connect()"

I then did

sudo apt-get install php5-mysql



i see 

/usr/lib/php5/mysql.so and mysqli.so


i have installed php5 in 

/usr/local/php

and apache2 resides
on

/usr/local/apache2


can someone point me in the right direction...


thanks...

---

### Post by jtc on 2007-04-18
Judging by the paths you supplied I guess you've installed apache and php manually?

Might it be so that php looks for mysql.so in /usr/local/lib/php (or similiar) instead? Are there any mysql-entries in your php.ini?

---

