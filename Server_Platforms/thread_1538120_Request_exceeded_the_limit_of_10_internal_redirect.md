---
title: "Request exceeded the limit of 10 internal redirects due to probable configuration"
date: 2010-07-24
forum: Server Platforms
---

### Post by OOzypal on 2010-07-24
Hello,

I am getting this error in any website in my ubuntu 10.4 local server. Even if the web site is a single index.html file. For example, if the domain is 

[www.test.loc](www.test.loc)

and I write [www.test.loc/index.html](www.test.loc/index.html), the site works ok but if I write only

[www.test.loc](www.test.loc)

I get this error
```
Sat Jul 24 22:00:54 2010] [error] [client 192.168.1.2] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace.
[Sat Jul 24 22:00:54 2010] [debug] core.c(3063): [client 192.168.1.2] r->uri = /home/hab/index.php
[Sat Jul 24 22:00:54 2010] [debug] core.c(3069): [client 192.168.1.2] redirected from r->uri = /home/hab/index.php
[Sat Jul 24 22:00:54 2010] [debug] core.c(3069): [client 192.168.1.2] redirected from r->uri = /home/hab/index.php
[Sat Jul 24 22:00:54 2010] [debug] core.c(3069): [client 192.168.1.2] redirected from r->uri = /home/hab/index.php
[Sat Jul 24 22:00:54 2010] [debug] core.c(3069): [client 192.168.1.2] redirected from r->uri = /home/hab/index.php
[Sat Jul 24 22:00:54 2010] [debug] core.c(3069): [client 192.168.1.2] redirected from r->uri = /home/hab/index.php
[Sat Jul 24 22:00:54 2010] [debug] core.c(3069): [client 192.168.1.2] redirected from r->uri = /home/hab/index.php
[Sat Jul 24 22:00:54 2010] [debug] core.c(3069): [client 192.168.1.2] redirected from r->uri = /home/hab/index.php
[Sat Jul 24 22:00:54 2010] [debug] core.c(3069): [client 192.168.1.2] redirected from r->uri = /home/hab/index.php
[Sat Jul 24 22:00:54 2010] [debug] core.c(3069): [client 192.168.1.2] redirected from r->uri = /home/hab/index.php
[Sat Jul 24 22:00:54 2010] [debug] core.c(3069): [client 192.168.1.2] redirected from r->uri = /
[Sat Jul 24 22:00:54 2010] [debug] mod_deflate.c(615): [client 192.168.1.2] Zlib: Compressed 613 to 379 : URL /home/hab/index.php
```

I don't know why things are redirected from /home/hab/index.php even though my web server is at 

```
/home/hab/www/html/test
```

Note: I change LogLevel to Debug.

Can you please help me?

TIA

---

