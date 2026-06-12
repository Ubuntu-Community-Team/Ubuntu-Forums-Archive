---
title: "xinetd"
date: 2007-08-09
forum: Server Platforms
---

### Post by raylu on 2007-08-09
1. Why is xinetd not widely adopted? Googling around gives me lots of results for configuring inetd. Is it similar to the OMG-it's-so-critical-so-we-shouldn't-mess-with-it-like-apache1.3 argument?

2. Like [these guys](http://ubuntuforums.org/showthread.php?t=291169), I'm wondering if there's a place to find configurations for common servers/daemons.

3. Some people say that Apache2 shouldn't be run in inetd mode; why is this? Is the startup time on apache slow enough that it's noticable? I run a small server, mostly for myself, that gets 10 hits on a busy day; should I leave it as standalone anyway?

4. As far as I can tell, mysqld shouldn't be run as anything but standalone; Googling draws a blank. Is this true?

5. What other services should I run with xinetd? (I'm thinking of configuring sshd for this, but I'm not at the computer right now and am using ssh to do this, so if I screw it up...)
```
tcp        0      0 localhost:2208          *:*                     LISTEN
tcp        0      0 *:swat                  *:*                     LISTEN
**tcp        0      0 localhost:6600          *:*                     LISTEN**
tcp        0      0 localhost:mysql         *:*                     LISTEN
tcp        0      0 *:netbios-ssn           *:*                     LISTEN
tcp        0      0 *:www                   *:*                     LISTEN
tcp        0      0 *:ftp                   *:*                     LISTEN
**tcp        0      0 localhost:ipp           *:*                     LISTEN**
tcp        0      0 *:smtp                  *:*                     LISTEN
tcp        0      0 *:https                 *:*                     LISTEN
**tcp        0      0 localhost:2207          *:*                     LISTEN**
tcp6       0      0 *:ssh                   *:*                     LISTEN
tcp6       0      0 *:9367                  *:*                     LISTEN
```
What are those and why do I need them? Why is a SMTP server running?

---

