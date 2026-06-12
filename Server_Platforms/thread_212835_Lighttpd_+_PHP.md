---
title: "Lighttpd + PHP"
date: 2006-07-10
forum: Server Platforms
---

### Post by huwnet on 2006-07-10
I have installed lighttpd, mod_fastcgi and the relevant php files. However when I try to open a php in lighttpd I just get a blank file.

Here is my fastcgi config:

```
fastcgi.server    = ( ".php" =>
                       ( "localhost" => 
                        (
                          "bin-path" => "/usr/bin/php5-cgi",
                          "port" => 9000
                        )
                      )
                    )

```

Obviously the module is enabled ;)

---

### Post by firecat53 on 2006-07-12
Here's my /etc/lighttpd/conf-enabled/10-fastcgi.conf:

```
fastcgi.server = ( ".php" => ((
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

Hope that helps!

I managed to get lighttpd working with mysql, php5 (w/ fastcgi) and python (normal cgi). 

Good luck!   Scott

---

### Post by huwnet on 2006-07-30
Thanks.

Now if only this could be fixed in the default packages :D

---

