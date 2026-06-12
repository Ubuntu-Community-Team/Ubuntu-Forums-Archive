---
title: "Apache 2.4 + mod_itk + FCGI Script not working"
date: 2017-05-03
forum: Server Platforms
---

### Post by infecticide2 on 2017-05-03
I have setup my Apache 2.4 instance such that each domain runs as its own user with mod_itk successfully until now.

I have discovered that my QGIS Map Server (/usr/lib/cgi-bin/project/qgis_mapserv.fcgi) is not functioning.

The Apache logs display a couple of these:

```

[fcgid:warn] [pid 18444] [client 24.222.173.58:49767] mod_fcgid: can't apply process slot for /usr/lib/cgi-bin/project/qgis_mapserv.fcgi

```

Before returning a 503 Service Unavailable to the browser



Config Snippit:

```

        Alias "/wms/" "/usr/lib/cgi-bin/project/qgis_mapserv.fcgi"
        ScriptAlias /wms/ /usr/lib/cgi-bin/project/
        <Directory /usr/lib/cgi-bin/project>
                AllowOverride All
                Options +ExecCGI -MultiViews +FollowSymLinks
                Require all granted
        </Directory>


```

I've read in a few places about mpm_itk not being compatible with FCGI scripts and other places mention using suexec which didn't seem to work for me.

Any ideas?

---

### Post by infecticide2 on 2017-05-03
I've revamped the config to try and setup suexec but still having the same issue:

```

<VirtualHost *:443>
        AssignUserID    forgottenlives forgottenlives

        Alias "/wms" "/var/www/forgottenlives.ca/cgi-bin"
        ScriptAlias /wms /var/www/forgottenlives.ca/cgi-bin
        SuexecUserGroup forgottenlives forgottenlives
        <Directory /var/www/forgottenlives.ca/cgi-bin>
                FCGIWrapper /var/www/forgottenlives.ca/cgi-bin/qgis_mapserv .fcgi
                AllowOverride All
                Options +ExecCGI -MultiViews +FollowSymLinks
                Require all granted
        </Directory>

```


Directory permissions:

```

:/var/www/forgottenlives.ca/cgi-bin# ls -hal
total 1.7M
drwxrwx--- 1 forgottenlives forgottenlives   94 May  3 20:09 .
drwxrwx--- 1 forgottenlives forgottenlives  142 May  3 19:19 ..
-rwx------ 1 forgottenlives forgottenlives 275K May  3 19:36 Forgottenlives.qgs
-rwx------ 1 forgottenlives forgottenlives   68 May  3 20:09 qgis_mapserv
-rwx------ 1 forgottenlives forgottenlives 1.4M May  3 19:42 qgis_mapserv.fcgi

```

---

### Post by infecticide2 on 2017-05-04
I've increased the logging on mod_fcgid and now it shows the following errors:

```

[fcgid:debug] [pid 10054] fcgid_proc_unix.c(542): (13)Permission denied: [client 24.222.173.58:51581] mod_fcgid: can't connect unix domain socket: /var/lib/apache2/fcgid/sock/10033.4

```

Directory permissions:

```

/var/lib/apache2/fcgid/sock# ls -hal
total 0
drwxr-xr-x 1 www-data www-data  0 May  3 22:13 .
drwxr-xr-x 1 www-data www-data 14 May  3 22:11 ..

```

It seems the sockets are being created with "www-data" 0700 instead of "forgottenlives".

---

