---
title: "Lighttpd Problem"
date: 2007-02-07
forum: Server Platforms
---

### Post by garethppls on 2007-02-07
[QUOTE=Konsole]$Starting lighttpd: 2007-02-07 19:53:13: (plugin.c.255) dlopen() failed for: /usr/local/lib/mod_fastcgi.so /usr/local/lib/mod_fastcgi.so: undefined symbol: http_chunk_append_file
2007-02-07 19:53:13: (server.c.1119) loading plugins finally failed
[/QUOTE]

on starting Lighttpd, it gives me this error in relation to FastCGI and its only that module that its having difficulty with when I comment it its fine, but I really want to use PHP with it.

---

### Post by odejoy on 2007-03-20
I am getting a similar error:

```

/etc/init.d/lighttpd start

* Starting web server lighttpd                                             

2007-03-20 17:39:47: (plugin.c.254) dlopen() failed for: /usr/lib/mod_fastcgi.so /usr/lib/mod_fastcgi.so: undefined symbol: http_chunk_append_file 

2007-03-20 17:39:47: (server.c.1174) loading plugins finally failed

```

Any ideas??

Thanks!

---

### Post by firecat53 on 2007-06-30
Not sure if this answers your question (and it's a few months late) but for information, here's my working etc/lighttpd/conf-enabled/10-fastcgi.conf file:

```
server.modules   += ( "mod_fastcgi" )

## Start an FastCGI server for php5 (needs the php5-cgi package)
fastcgi.server = (  ".php" => ((
                     "bin-path" => "/usr/bin/php-cgi",
                     "socket" => "/tmp/php.socket",
                     "max-procs" => 1,
                     "bin-environment" => (
                       "PHP_FCGI_CHILDREN" => "8",
                       "PHP_FCGI_MAX_REQUESTS" => "10000"
                     ),
                     "bin-copy-environment" => (
                       "PATH", "SHELL", "USER"
                     ),
                     "broken-scriptfilename" => "enable"
                   )))

```

A lot of lightpd errors stem from configuration issues. Let me know if you have other (mmm...basic) lighttpd questions. 

Scott

---

