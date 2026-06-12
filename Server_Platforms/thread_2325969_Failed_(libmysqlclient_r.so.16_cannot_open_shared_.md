---
title: "Failed (libmysqlclient_r.so.16: cannot open shared object file:"
date: 2016-05-27
forum: Server Platforms
---

### Post by NoryElpido on 2016-05-27
Hello,

I'am trying to run my MySQL based sa-mp server on linux ubuntu but i'am keep getting this error
[COLOR=#000000][FONT=verdana][25/05/2016 10:40:47] Failed (libmysqlclient_r.so.16: cannot open shared object file: No such file or directory)

[/FONT][/COLOR]I already posted help on sa-mp forums but they weren't able to help, I'd just like to know how do i able to sort this up? How do i fix it ? Some is telling me that libmysqlclient_r.so.16 is not available on Ubuntu 14.04 anymore, Which i'm generally confused. If you can help me out how to install libmysqlclient_r.so.16 I'm very grateful then..

OS: Ubuntu
Distro: Ubuntu 14.04x64 (10gb)

---

### Post by howefield on 2016-05-27
Moved to the "*Server Platforms*" for a better fit.

---

### Post by NoryElpido on 2016-05-27
Thank you, I appreciate it

---

### Post by nerdtron on 2016-05-30
Did you installed the libmysqlclient-dev package? I believe this package contains the [COLOR=#000000][FONT=verdana]libmysqlclient_r.so library the you need.

Reference here:[http://packages.ubuntu.com/trusty/libmysqlclient-dev](http://packages.ubuntu.com/trusty/libmysqlclient-dev)
[/FONT][/COLOR]

---

