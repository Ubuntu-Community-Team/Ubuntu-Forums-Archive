---
title: "server 64"
date: 2007-10-16
forum: Server Platforms
---

### Post by ae+ on 2007-10-16
just wondering what the general consensus is on running a 64 bit version of ubuntu for servers? is it there yet?

to be more specific, a web server with the following:
- php
- mysql
- bind
- subversion
- samba
- java
- tomcat
- apache2

thanks for any advice

andrew

---

### Post by elvis on 2007-10-16
I run64bit versions of all of the above in production environments on x86_64 hardware, and have done so for some time now.

Generally speaking, the vast majority of free software tools were ported to 64bit very quickly.  The only real problems that still exist for 64bit Linux are generally non-free tools (Macromedia/Adobe Flash, for example.  Ditto for a lot of binary-only, non-free drivers).

If you are building a server with 100% free software, feel safe knowing it will work fine in a 64bit environment.

---

### Post by ae+ on 2007-10-16
thanks for the reply - i appreciate it  :)

---

