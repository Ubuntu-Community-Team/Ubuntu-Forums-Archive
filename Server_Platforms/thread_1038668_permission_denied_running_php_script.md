---
title: "permission denied running php script"
date: 2009-01-13
forum: Server Platforms
---

### Post by uvdevnull on 2009-01-13
Trouble running a PHP-based script.
It's actually a plugin to Nagios called check_mssql but that probably doesn't make a difference.
When I first started, I didn't have the PHP interpreter, so got that installed.
Then the script header pointed to a different directory, so got that corrected.  But still, problems persist...
```
[app04: /usr/local/nagios/libexec]$ sudo ./check_mssql
sudo: unable to execute ./check_mssql: Permission denied
```
Header of the script:
```

[app04: /usr/local/nagios/libexec]$ cat check_mssql
#!/usr/lib/php5/
<?php
############################################################################
#
# check_mssql - Checks various aspect of MSSQL servers
#
# Version 0.6.6, [OUTPUT TRUNCATED]
```
PHP location:
```
[app04: /usr/local/nagios/libexec]$ whereis php5
php5: /etc/php5 /usr/lib/php5 /usr/share/php5
```
Script permissions:
```
[app04: /usr/local/nagios/libexec]$ ls -l |grep mssql
-rwxr-xr-x 1 nagios nagios  11429 2009-01-13 14:51 check_mssql
```
This is what I got before changing the header to the correct path, or at least an existent path:
```
sudo: unable to execute ./check_mssql: No such file or directory
```
But I'm clueless how to fix this.  Any pointers appreciated!

---

### Post by gombadi on 2009-01-14
From the file -

```

#!/usr/lib/php5/

```

The location of the executable -
```

/usr/lib/php5

```

Spot the difference or just remove the trailing /

---

### Post by uvdevnull on 2009-01-14
I think I had it without the trailing "/" before, but this makes no difference.

Also, I don't have a php5 file under /usr/lib, only a directory:
```
[app04: /usr/local/nagios/libexec]$ ls /usr/lib |grep php && file /usr/lib/php5
php5
/usr/lib/php5: directory

[app04: /usr/local/nagios/libexec]$ tree /usr/lib/php5
/usr/lib/php5
|-- 20060613+lfs
|   |-- mysql.so
|   |-- mysqli.so
|   |-- pdo.so
|   `-- pdo_mysql.so
|-- libexec
`-- maxlifetime
```
Is that all that should be in there? Seems rather bare. Perhaps I don't have PHP fully installed?
I just did "sudo apt-get install php5" and "sudo apt-get install php5-mysql".

---

### Post by gombadi on 2009-01-14
> 
I just did "sudo apt-get install php5" and "sudo apt-get install php5-mysql"


To run php5 from the commandline you need the php5-cli package

After installing that package do a which php5 to find the location of the executable.

---

### Post by uvdevnull on 2009-01-14
Thanks brother, that did it! :D

Btw, perhaps I might have actually figured that out, but when I searched for packages containing php5, I did not get php5-cli listed, nor some of the others I needed later.
I was using
```
[app04: /usr/local/nagios/libexec]$ dpkg-query -l 'php*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                Version             Description
+++-===================-===================-======================================================
un  php-pear            <none>              (no description available)
un  php4-mysql          <none>              (no description available)
ii  php5                5.2.6-2ubuntu4      server-side, HTML-embedded scripting language (metapac
un  php5-cgi            <none>              (no description available)
ii  php5-common         5.2.6-2ubuntu4      Common files for packages built from the php5 source
un  php5-json           <none>              (no description available)
ii  php5-mysql          5.2.6-2ubuntu4      MySQL module for php5
un  php5-mysqli         <none>              (no description available)
un  php5-timezonedb     <none>              (no description available)
un  phpapi-20060613+lfs <none>              (no description available)
```
which gave me incomplete results.
So now I did "aptitude search php5" and got the full list. "apt-cache search php5" works too.
Not sure where I picked up the dpkg-query line, but I guess I'll stop using now... :)

---

