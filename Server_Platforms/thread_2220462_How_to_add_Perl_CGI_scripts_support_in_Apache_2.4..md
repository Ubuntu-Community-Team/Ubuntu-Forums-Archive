---
title: "How to add Perl CGI scripts support in Apache 2.4.7 / Ubuntu Server 14.04?"
date: 2014-04-28
forum: Server Platforms
---

### Post by insiki2 on 2014-04-28
Hello guys.
I installed lightsquid (reports for squid) and try to configure CGI scripts support in new version of apache2.
I added those strings in file /etc/apache2/sites-available/000-default.conf
```
 Alias /stats "/usr/lib/cgi-bin/lightsquid"
        <Directory /usr/lib/cgi-bin/lightsquid/>
        Options ExecCGI FollowSymLinks
        AddHandler cgi-script .cgi .pl
        AllowOverride All
        Require all granted
        </Directory>

```
But when i try to open page in browser i see a code of CGI script.
Can u help me?

---

### Post by Lars Noodén on 2014-04-28
Shouldn't that be [ScriptAlias](http://httpd.apache.org/docs/2.4/mod/mod_alias.html#scriptalias) instead?

```

ScriptAlias /stats /usr/lib/cgi-bin/lightsquid

```

Also, did you enable the CGI module?

```

sudo a2enmod cgi
sudo service apache2 restart

```

---

### Post by insiki2 on 2014-04-28
Thanks! It works! :))
Module does not was enabled.

---

### Post by insiki2 on 2014-04-30
Hm, next problem - *.php does not work

Apache error.log
```
[Wed Apr 30 11:09:00.979746 2014] [:error] [pid 31893] [client 192.168.1.200:64204] PHP Fatal error:  Call to undefined function connectdb() in /var/lib/bandwidthd/htdocs/sensors.php on line 27
[Wed Apr 30 11:09:04.695518 2014] [:error] [pid 31894] [client 192.168.1.200:64205] PHP Fatal error:  Call to undefined function connectdb() in /var/lib/bandwidthd/htdocs/sensors.php on line 27
[Wed Apr 30 11:09:05.991913 2014] [:error] [pid 31896] [client 192.168.1.200:64210] PHP Fatal error:  Call to undefined function connectdb() in /var/lib/bandwidthd/htdocs/sensors.php on line 27
[Wed Apr 30 11:09:07.912011 2014] [:error] [pid 31899] [client 192.168.1.200:64211] PHP Fatal error:  Call to undefined function connectdb() in /var/lib/bandwidthd/htdocs/sensors.php on line 27
[Wed Apr 30 11:09:17.375590 2014] [:error] [pid 31893] [client 192.168.1.200:64213] PHP Fatal error:  Call to undefined function connectdb() in /var/lib/bandwidthd/htdocs/sensors.php on line 27
[Wed Apr 30 11:09:18.156891 2014] [:error] [pid 31912] [client 192.168.1.200:64214] PHP Fatal error:  Call to undefined function connectdb() in /var/lib/bandwidthd/htdocs/sensors.php on line 27
[Wed Apr 30 11:09:18.380311 2014] [:error] [pid 31896] [client 192.168.1.200:64216] PHP Fatal error:  Call to undefined function connectdb() in /var/lib/bandwidthd/htdocs/sensors.php on line 27
[Wed Apr 30 11:11:18.160106 2014] [:error] [pid 31895] [client 192.168.1.200:64239] PHP Fatal error:  Call to undefined function connectdb() in /var/lib/bandwidthd/htdocs/sensors.php on line 27
[Wed Apr 30 11:11:18.476099 2014] [:error] [pid 31893] [client 192.168.1.200:64241] PHP Fatal error:  Call to undefined function connectdb() in /var/lib/bandwidthd/htdocs/sensors.php on line 27
[Wed Apr 30 11:11:18.684193 2014] [:error] [pid 31912] [client 192.168.1.200:64242] PHP Fatal error:  Call to undefined function connectdb() in /var/lib/bandwidthd/htdocs/sensors.php on line 27
[Wed Apr 30 11:11:18.873014 2014] [:error] [pid 31896] [client 192.168.1.200:64243] PHP Fatal error:  Call to undefined function connectdb() in /var/lib/bandwidthd/htdocs/sensors.php on line 27
[Wed Apr 30 11:11:19.048865 2014] [:error] [pid 31899] [client 192.168.1.200:64244] PHP Fatal error:  Call to undefined function connectdb() in /var/lib/bandwidthd/htdocs/sensors.php on line 27
[Wed Apr 30 11:11:19.225919 2014] [:error] [pid 31892] [client 192.168.1.200:64240] PHP Fatal error:  Call to undefined function connectdb() in /var/lib/bandwidthd/htdocs/sensors.php on line 27
[Wed Apr 30 11:11:19.417101 2014] [:error] [pid 31895] [client 192.168.1.200:64246] PHP Fatal error:  Call to undefined function connectdb() in /var/lib/bandwidthd/htdocs/sensors.php on line 27
[Wed Apr 30 11:15:09.033771 2014] [:error] [pid 31899] [client 192.168.1.200:64308] PHP Fatal error:  Call to undefined function connectdb() in /var/lib/bandwidthd/htdocs/sensors.php on line 27
[Wed Apr 30 11:23:04.806419 2014] [:error] [pid 31893] [client 192.168.1.200:53236] PHP Fatal error:  Call to undefined function connectdb() in /var/lib/bandwidthd/htdocs/sensors.php on line 27

```

---

