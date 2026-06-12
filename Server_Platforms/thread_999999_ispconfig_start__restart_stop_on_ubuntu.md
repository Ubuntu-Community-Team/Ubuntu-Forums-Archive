---
title: "ispconfig start | restart| stop on ubuntu"
date: 2008-12-02
forum: Server Platforms
---

### Post by jarco5000 on 2008-12-02
this is probably very basic but i can't seem to find it.
I have a ubuntu server 8.04 with ispconfig installed. when i browse to the ip apache returns the It works thingie but when i try to go to port 81 it just sais there is nothing there (on http and https). 
i figured ispconfig is not started (i am new to linux administration so i don't yet know how to see if it is) but cannot find the way to start it. I only find the commands for RedHat &  Mandrake (/etc/rc.d/init.d/ispconfig_server start|stop|restart and for SuSE & Debian (/etc/init.d/ispconfig_server start|stop|restart). When i use the command for debian it just sais the file aint there.

Anyone knows to start it on ubuntu?

---

### Post by trentscott4 on 2008-12-03
I setup my ISPConfig using the guide here (might be a good reference for you):

[http://www.howtoforge.com/perfect-server-ubuntu-8.10](http://www.howtoforge.com/perfect-server-ubuntu-8.10)

As far as the command you're looking for, try:

```
/etc/init.d/ispconfig_server start|stop|restart
```

Good luck!

Trent

---

