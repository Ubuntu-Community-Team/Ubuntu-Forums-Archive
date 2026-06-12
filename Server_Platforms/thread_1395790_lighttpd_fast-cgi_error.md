---
title: "lighttpd fast-cgi error"
date: 2010-02-01
forum: Server Platforms
---

### Post by skaramanger on 2010-02-01
Greetings,

Any idea what the following error message is about:

sudo /etc/init.d/lighttpd force-reload
Duplicate config variable in conditional 0 global: fastcgi.server
2010-02-01 10:06:13: (configfile.c.864) source: /etc/lighttpd/lighttpd.conf line: 172 pos: 1 parser failed somehow near here: (EOL) 

Position 172 is past the eof.

This little project started out as just an idea to be able to view my ups status via multimon.cgi. I install lighttpd, PHP5, mysql according to this link:

[URL=http://www.ubuntugeek.com/lighttpd-webserver-setup-with-php5-and-mysql-support.html[/URL]

I enabled cgi and fastcgi.  
Then sudo /etc/init.d/lighttpd force-reload gives the above error message.
Any suggestions?

Thanks,

---

### Post by skaramanger on 2010-02-01
Just an update I got multimon.cgi to work and can view my ups status locally. Yaa!  I added mod_cgi to the lighttpd.conf file and it now works..

Still like to know about fastcgi_mod problem thanks

---

