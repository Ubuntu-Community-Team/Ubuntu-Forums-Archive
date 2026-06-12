---
title: "php-zeroc-ice and lighttpd"
date: 2009-03-29
forum: Server Platforms
---

### Post by endeavormac on 2009-03-29
I am trying to use the php-zeroc-ice package to get support for [http://www.zeroc.com/](http://www.zeroc.com/) in php. The web server I'm using is lighttpd. For some reason, when I ```
apt-get install php-zeroc-ice
``` lighttpd refuses to start properly. I don't get any errors from lighttpd, but it doesn't start either.

Here is relevant parts of my lighttpd.conf:
```

            "mod_fastcgi"
)

fastcgi.server = ( ".php" => ((
                   "bin-path" => "/usr/bin/php5-cgi",
                   "socket" => "/tmp/php.socket"
               )))

```

Ubuntu Intrepid amd64

Thoughts?

---

### Post by Thomas_ on 2009-04-17
Same problem, same ubuntu version.

PHP segfaults, but only when it loads Murmur.ice,  ICE alone runs fine

a 64-bit issue?

---

### Post by KingPin6 on 2009-04-17
same here, ubuntu 8.10 x86_64 php crashes if loaded with murmur slice. using lighty also.

---

### Post by bluewish on 2012-06-28
Don't suppose there's a fix for this? I'm running Debian Squeeze 64bit and same problem.

---

