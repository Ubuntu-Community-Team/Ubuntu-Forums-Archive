---
title: "Apache2 Start Fail: undefined symbol"
date: 2011-06-19
forum: Server Platforms
---

### Post by acetech09 on 2011-06-19
I installed apache2 using synaptic, getting the prefork mpm.

When I tried to start it with /etc/init.d/apache2 start, I get following error:

```
* Starting web server apache2
/usr/sbin/apache2: symbol lookup error: /usr/sbin/apache2: undefined symbol: apr_os_uuid_get

```

I've reinstalled libapr, libaprutils, checked versions of libapr, completely removed then reinstalled apache, and have had no luck in trying to fix this.


Anybody have any ideas? My business' server is down until I fix this.

---

### Post by maykofaria on 2011-09-29
bump

Ran out in the same problem and can't find a solution

---

### Post by TravisZ on 2011-10-02
Hopefully this will help:

[http://www.factsandpeople.com/facts-mainmenu-5/26-html-and-javascript/134-compiling-apache-webserver-on-linux](http://www.factsandpeople.com/facts-mainmenu-5/26-html-and-javascript/134-compiling-apache-webserver-on-linux)

Not sure if you are installing APR manually but a make clean before compiling with make seemed to help this person.

---

