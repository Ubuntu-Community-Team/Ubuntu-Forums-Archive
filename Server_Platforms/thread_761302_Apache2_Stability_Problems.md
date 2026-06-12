---
title: "Apache2 Stability Problems"
date: 2008-04-21
forum: Server Platforms
---

### Post by John Clayton on 2008-04-21
Running an Ubuntu 7.10 Server VM (on an Ubuntu 7.10 server host), using it as a LAMP server with Nagios, Drupal and a few other web apps installed.  The virtual machine has a 512 meg of RAM and more than enough hard drive space.  However, Apache2 seems to be very unstable.  For instance, when a user accesses TikiWiki (at <serverIP>/wiki, theres a 50-50 chance they'll get the wiki homepage or the following error:
```
Invalid Command Sent:GET http://serverIP/wiki HTTP/1.1
Connection: close
User-Agent: Mozilla/5.0 (compatible; Konqueror/4.0; Linux) KHTML/4.0.3 (like Gecko)
Accept: text/html, image/jpeg, image/png, text/*, image/*, */*
Accept-Encoding: x-gzip, x-deflate, gzip, deflate
Accept-Charset: utf-8, utf-8;q=0.5, *;q=0.5
Accept-Language: en-US, en
Host: 10.215.1.86
Cookie: tz_offset=3600

```
This happens whether the browser is konqueror, firefox, opera, whatever and both on Linux and windows.

Anyone got any clues?

---

### Post by craigp84 on 2008-04-29
Hi John,

That's very interesting. Do you have any non standard modules loaded; like mod_php or mod_perl etc?

Does the apache error log give any more detail?

-c

---

