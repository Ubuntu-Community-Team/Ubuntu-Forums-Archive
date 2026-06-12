---
title: "apache2 vhost &amp; VLOG"
date: 2006-05-15
forum: Server Platforms
---

### Post by cvmiller on 2006-05-15
My apologies if this has already been addressed.

I am running ubuntu 6.0 beta (which shouldn't matter) and Apache2 2.0.54. I am trying to migrate from my mandrake PPC system to the ubuntu PPC.

I have set up a virtual host, which responds nicely. However I am unable to get the access log to work correctly. That is I am used to using the Setenv VLOG statement in the vhost file and have apache2 automagically create a log for me for that virtual host (works this way on my Mandrake system with apache 2.0.53).

In my vhost file I have the following:
        Setenv VLOG /var/log/apache2/

However this doesn't setup my logs in the supplied directory. Oddly this alone does set up my vhost logs on the "other" (read: mandrake) system.

What I am looking for are logs which are automatically rotated and prepended with the vhost name. Here's what they look like on my mandrake system:
/var/log/httpd/VLOG-2005-12-makiki.homelinux.net.log
/var/log/httpd/VLOG-2006-01-makiki.homelinux.net.log
/var/log/httpd/VLOG-2006-02-makiki.homelinux.net.log
/var/log/httpd/VLOG-2006-03-makiki.homelinux.net.log
/var/log/httpd/VLOG-2006-04-makiki.homelinux.net.log
/var/log/httpd/VLOG-2006-05-makiki.homelinux.net.log

Is there a way to do this via the vhost file?

TIA,

Craig...

---

### Post by cvmiller on 2006-05-17
Apparently Mandrake has tweeked apache a bit to make it more virtual host friendly. I found that if I use a more standard logging command, such as:
CustomLog  "| /usr/sbin/rotatelogs /var/log/apache2/VLOG-%Y-%m-%d-myserver.com.log 604800" combined

This will rotate the log once a week, and tag the log name with Year, Month, and Date.

---

