---
title: "Wordpress needs x11-common?"
date: 2008-05-07
forum: Server Platforms
---

### Post by weyh on 2008-05-07
I have a 8.04 server set up with apache2 and was looking to install  Wordpress on it. So I checked the repositories and it's there but wants to install a number of libraries which I expect but I wonder why it wants x11 stuff like x11-common when there is no X11 server on the server.

Am I missing something?


Thanks,
D

---

### Post by koenn on 2008-05-07
aparently it doesn't require x-common :
[http://packages.ubuntu.com/hardy/web/wordpress](http://packages.ubuntu.com/hardy/web/wordpress)

you could check the dependencies of the actual package with
```
 apt-cache show wordpress
```
and possibly mail the packager and ask if you find dependencies there that don't make sense. 

It's also possible that x-common is a dependencie of 1 of the dependencies of wordpress. You could check those to (on the web or via apt-cache)

---

### Post by weyh on 2008-05-07
yea it seems to be the php5-gd package that triggers it.

I just did a download and install from wordpress.org

Thanks for your help,
D

---

