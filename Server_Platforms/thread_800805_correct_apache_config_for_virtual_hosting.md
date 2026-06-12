---
title: "correct apache config for virtual hosting"
date: 2008-05-20
forum: Server Platforms
---

### Post by jbc-wales on 2008-05-20
I followed the tutorial here:
[https://help.ubuntu.com/community/ApacheMySQLPHP ]("https://help.ubuntu.com/community/ApacheMySQLPHP")

on setting up a localhost / lamp-stack.

I got to the point where it reports a message saying "It is working." Everything fine on that front.

However, when I tried to restart Apache, I received the following error message, which I cannot understand:

```
open: Permission denied
 * Restarting web server apache2                                                httpd (pid 6139?) not running
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
open: Permission denied

```

Can anyone point me in the right direction for resolving this permission denied error?

Thanks!


UPDATE: I forgot to sudo my apache restart command

---

### Post by Donb01 on 2008-05-20
It looks like in your Vhosts.conf file that when you were setting up your virtual hosts you made a typo of the IP address for your default destination (or one of the other virtual hosts).  Look in there first and see if anything looks out of place.

---

