---
title: "php4-pear requires php5-common?"
date: 2006-09-17
forum: Repositories &amp; Backports
---

### Post by WesleyWex on 2006-09-17
I see that php4-pear requires php4-common, like shown in the [ubuntu packages list]("http://packages.ubuntu.com/dapper/web/php4-pear").

But apt-get is saying other thing:
```
root@servidor:/home/wesley/Downloads# apt-get install php4-pear
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  php-db php-http php-mail php-net-smtp php-net-socket php-pear php-xml-parser php5-common
Recommended packages:
  php-auth-sasl
The following NEW packages will be installed
  php-db php-http php-mail php-net-smtp php-net-socket php-pear php-xml-parser php4-pear php5-common
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/618kB of archives.
After unpacking 3924kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

Why does it want to install php**5**-common?

---

