---
title: "PHP5-Sybase - MSSQL_CONNECT()"
date: 2012-09-26
forum: Server Platforms
---

### Post by bravoslayer on 2012-09-26
Hey guys.


I have the following problem and need a fast fix. 

I did install "php5-mssql" on my server to start running cronjobs from PHPCLI which was working completely fine until one day.


My Cronjob kept failing with errors about PHP library could not be loaded. I narrowed it down to mssql. I uninstalled the packed by using: sudo apt-get remove php5-mssql

then restart apache: /etc/init.d/apache2 restart 

I then ran an installation of php5-mssql again. 

> root@bravosl:~# sudo apt-get install php5-mssql
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'php5-sybase' instead of 'php5-mssql'
The following packages were automatically installed and are no longer required:
  gamin bind9utils libdns66 maildrop libisccc60 geoip-database libgamin0
  sensible-mda courier-ssl liblwres60 expect courier-base libbind9-60
  courier-authlib-userdb courier-authlib tcl8.5 libgeoip1 libisccfg60 libisc60
  courier-authdaemon
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  php5-sybase
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/23.2kB of archives.
After this operation, 123kB of additional disk space will be used.
Selecting previously deselected package php5-sybase.
(Reading database ... 21571 files and directories currently installed.)
Unpacking php5-sybase (from .../php5-sybase_5.3.3-1ubuntu9.10_i386.deb) ...
Processing triggers for libapache2-mod-php5 ...
 * Reloading web server config apache2                                          [Wed Sep 26 21:34:04 2012] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
                                                                         [ OK ]
Setting up php5-sybase (5.3.3-1ubuntu9.10) ...
root@bravosl:~#
Ever since then, I have noticed that php5-sybase gets installed without the functions that I am looking for (mssql_connect)


I have collected the following logs to share: 

> root@bravosl:~#dmesg 
179921.031720] php[19676]: segfault at ff ip b6b9836a sp bfa6c150 error 6 in ms                                                                           sql.so[b6b94000+9000]
[179981.135023] php[19684]: segfault at ff ip b6b6836a sp bf9eb290 error 6 in ms                                                                           sql.so[b6b64000+9000]


> root@bravosl:~#cat /var/log/apache2/error.log | grep mssql 
[Tue Sep 25 16:47:21 2012] [error] [client 109.170.137.202] PHP Fatal error:  Call to undefined function mssql_connect() in /var/www/mssql.php on line 8, referer: [http://www.nightsfall-online.com/index.php](http://www.nightsfall-online.com/index.php)
[Tue Sep 25 17:20:16 2012] [error] [client 109.170.137.202] PHP Fatal error:  Call to undefined function mssql_connect() in /var/www/mssql.php on line 8
[Tue Sep 25 20:05:13 2012] [error] [client 94.168.105.102] PHP Fatal error:  Call to undefined function mssql_connect() in /var/www/mssql.php on line 8
[Tue Sep 25 20:35:34 2012] [error] [client 94.168.105.102] PHP Fatal error:  Call to undefined function mssql_connect() in /var/www/mssql.php on line 8
root@bravosl:~#

I have checked for the functions of mssql_connect exist by using the standard PHP script to check for present functions. They are not present. 

The question I am asking, is how do i get the mssql extension to work again

---

### Post by SeijiSensei on 2012-09-26
I don't have an Ubuntu server running PHP at the moment to check, but I'm pretty sure that you need to tell PHP to load extra modules like Sybase for the command-line executable.  Root around in /etc/php5 and see what you find.  There should be files that load the .so files that contain the additional modules.  You may need to clone the one in /etc/php5/apache2 so it works with the command-line executable as well.

Create a file called info.php with the single line "<?php phpinfo() ?>" and run it with the command-line executable.  Do you see the Sybase modules loaded there?  What if you access the same file through Apache?

---

