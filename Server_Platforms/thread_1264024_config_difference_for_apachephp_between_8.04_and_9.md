---
title: "config difference for apache?php? between 8.04 and 9.04"
date: 2009-09-11
forum: Server Platforms
---

### Post by speed145a on 2009-09-11
does anyone know why this is happening?  I have a development system, and a server.  the development system is ubuntu 9.04, and the server is 8.04.3

I wrote some code for my web server and got it working on the dev system, when i moved the code up to the server, it's not working the same.

when looking at the source code of the page i've found that the server (8.04.3) is prepending the absolute path before many elements.

so, when i had referenced in my code
```
'http://SERVER.com/absolute/path/to/my/element.jpg'
```
and that worked as shown on 9.04, on the server it ended up looking like this:
```
'http://SERVER.com/absolute/path/to/http://SERVER.com/absolute/path/to/my/element.jpg'
```


any ideas where to look?  :confused:

---

