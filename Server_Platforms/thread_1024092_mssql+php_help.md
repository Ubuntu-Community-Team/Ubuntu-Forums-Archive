---
title: "mssql+php help"
date: 2008-12-28
forum: Server Platforms
---

### Post by warren.burstein on 2008-12-28
I've got a Hardy server that accesses MSSQL servers in Python.  I want to access one of them from PHP.  I'm not sure if the problem is with the packages that I've installed, the configuration files, my PHP code, or me.

Here's the python that works
```
#!/usr/bin/python
import pymssql
con = pymssql.connect(host = 'stnivr', user = 'user',
                      password = 'password', database = 'IVR'
```

And here's the PHP that fails (I'm running it by hand, not in apache)
```
<?php
$server = 'stnivr';
$link = sybase_connect($server, 'user', 'password')
        or die("Could not connect to $server!");
echo "Connected successfully";
sybase_close($link);
?>
```
It prints> Warning: sybase_connect(): Unable to connect to server:  stnivr in /home/warren/i.php on line 3

I wasn't sure if I needed to put an entry in /etc/freetds/freetds.conf, but this is what I put there.  stnivr is defined in /etc/hosts.
```
[stnivr]
        host = stnivr
        port = 1433
        tds version = 8.0

```

I made sure that the packages freetds-dev, php5, and php5-sybase were up to date.

I don't even know if this is a question for the ubuntu forum, the php forum, the freetds forum, Microsoft, or whomever.

---

### Post by warren.burstein on 2008-12-29
Well, after much hacking, it's started working.  I can't figure out what I changed that made it work so I'm going to assume I just had a typo in the server name, user, or password.

Here's what I did in case anyone else needs to debug a freetds connection.

The first thing I did was run the tsql program that should comeswith freetds.  Only it's not part of the freetds-dev package.  Someone already reported this on Intrepid.

No big deal, **apt-get source freetds**, configure (took a few builds and some strace-ing to get the configure options to look for the config file where it's located on Hardy and probably any other Ubuntu,  **--prefix=/usr --sysconfdir=/etc/freetds**), run **freetds-0.63/src/apps/tsql -S stnivr -U user -P password**, that worked (it prints a prompt if it logs in, an error message if it can't, which I checked by giving it wrong values for each field).

Then I ran both tsql and php with TDSDUMP=filename in the environment (different names) and saw that at some stage I had removed the username from my php script (it was there when I wrote the previous post, really).  I put it back, and success.

I did not install the freetds libs that I compiled, so it's not working because I built the package from source.

---

