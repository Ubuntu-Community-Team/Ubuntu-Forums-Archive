---
title: "With apache2, browsing to localhost yields 404"
date: 2007-05-06
forum: Server Platforms
---

### Post by cgs1019 on 2007-05-06
I am running apache2 on feisty. When I start the server and browse to [http://localhost/](http://localhost/) I get a 404 error. The error log says ```
File does not exist: /htdocs
``` For some reason, my httpd.conf file contains nothing but commented lines

```
# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so
```

I can not find any indication of the existence of an htdocs directory on my system, nor a reference to it in any config files. I am inexperienced and thoroughly confused. Any help would be greatly appreciated.

---

### Post by Mark F on 2007-06-07
Im getting the same problem. Fresh install of Feisty LAMP. Did you find a solution?

---

### Post by mister_doctor on 2007-06-07
**cgs1019** Are you just trying to test basic http connectivity?

I recommend this guide, it helped me get the basics going:
[https://help.ubuntu.com/7.04/server/C/httpd.html](https://help.ubuntu.com/7.04/server/C/httpd.html)

Trust me that guide is quite good, the official one from apache is ***-backwards.

Aim to be able to display the "It works!" page before installing the other modules. One piece at a time...

Also, the config file you want is apache2.conf. httpd.conf isn't used anymore. Hence the line, 

# This is here for **backwards compatability** reasons. 

;)

Hope it helps a little. Time for me to tinker with mine some more

---

