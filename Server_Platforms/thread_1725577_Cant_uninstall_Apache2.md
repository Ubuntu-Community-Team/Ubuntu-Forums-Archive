---
title: "Cant uninstall Apache2"
date: 2011-04-09
forum: Server Platforms
---

### Post by GeissT on 2011-04-09
Hey everyone,

So i want to remove Apache2 so i can compile my own edited version. But when i do it says that it cant remove it. here is a 'log':

```
geisst@ubuntu:~$ sudo apt-get purge apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apache2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
geisst@ubuntu:~$ 

```

But when i goto 'http://localhost' it shows the default, 'IT WORKED' page. I removed the folder '/var/www' and it says on 'http://localhost' that its not there any more, and shows the version number for apache.

I have also removed all folders containing the words 'apache'. Still to no avail. I have stopped the service

```
geisst@ubuntu:~$ sudo apachectl stop
/usr/sbin/apachectl: 148: /usr/sbin/apache2: not found
Action 'stop' failed.
The Apache error log may have more information.
geisst@ubuntu:~$ 
```

The error is because i have removed the folder, but for som reason its still running.

Any help is appreciated.

GeissT

---

### Post by Neo@Matrix on 2011-04-09
Try to empty browser cash with ctrl+****+del before going to localhost.

---

### Post by Neo@Matrix on 2011-04-09
:) for some reason the "sh ! ft"  was censored :)

---

### Post by GeissT on 2011-04-11
Thanks for your suggestion Neo. Ill give it a try.

---

### Post by GeissT on 2011-04-11
That method worked, but the server is still there, i typed 'apachectl' in the terminal and it displays this:

> geisst@ubuntu:~$ apachectl
Usage: /usr/sbin/apachectl start|stop|restart|graceful|graceful-stop|configtest|status|fullstatus|help
       /usr/sbin/apachectl <apache2 args>
       /usr/sbin/apachectl -h            (for help on <apache2 args>)
geisst@ubuntu:~$ 

---

### Post by lisati on 2011-04-11
> **Neo@Matrix said:**
> :) for some reason the "sh ! ft"  was censored :)

Perhaps because the letter F was missing....? Shift should work.

---

