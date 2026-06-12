---
title: "Horrible PHP/MySQL Query Performance On Ubuntu Server 10.04"
date: 2010-08-07
forum: Server Platforms
---

### Post by neoform on 2010-08-07
I just did a clear install of Ubuntu Server 10.04 with the standard LAMP config..

Then I made a small script to test insert speeds into a table with 3 columns.

When I run the script on any of my other machines (centos and fedora), I get about 2000-3000 inserts per second.

On the Ubuntu machine, I get about 20 inserts per second (same exact script).

I tried switching the script to use sockets instead, but that changed nothing.

When I do mysql dumps and restores, mysql performs very well and loads 1,000,000 records into the table in about 20 seconds.

Why is PHP getting such awful query rates into mysql? (i tried using pdo and mysqli - they both get the same results).

Currently installed:

libmysqlclient16                5.1.41-3ubuntu12
mysql-client-5.1                5.1.41-3ubuntu12
mysql-client-core-5.1           5.1.41-3ubuntu12
mysql-common                    5.1.41-3ubuntu12
mysql-server                    5.1.41-3ubuntu12
mysql-server-5.1                5.1.41-3ubuntu12
mysql-server-core-5.1           5.1.41-3ubuntu12
php5-mysql                      5.3.2-1ubuntu4.2
libapache2-mod-php5             5.3.2-1ubuntu4.2
php-apc                         3.1.3p1-2
php5-cli                        5.3.2-1ubuntu4.2
php5-common                     5.3.2-1ubuntu4.2
php5-mysql                      5.3.2-1ubuntu4.2

---

