---
title: "Serious server hangups - MaxClient settings"
date: 2007-03-20
forum: Server Platforms
---

### Post by cap10kirk on 2007-03-20
I'm have some serious problems with my server hanging up. I do get about 3 to 4k visits a day on my server. I do get an error message about MaxClient settings. My server is a P4 2.4 gh, 512k ram. Apache 2.0 server, PHP 5.1.2, mysql 5.0.22. I'm a novice, so I'm stuck. Any help would be greatly appreciated.

Kirk

Here is my httpd conf settings: 
Timeout 300

KeepAlive On

MaxKeepAliveRequests 0

KeepAliveTimeout 15

MinSpareServers 15
MaxSpareServers 20

StartServers 15

MaxClients 1000

MaxRequestsPerChild 0

Here is the errors that i get in my log:
[Tue Mar 20 11:55:38 2007] [notice] caught SIGTERM, shutting down
[Tue Mar 20 11:55:39 2007] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec2)
[Tue Mar 20 11:55:39 2007] [notice] FastCGI: process manager initialized (pid 7965)
[Tue Mar 20 11:55:40 2007] [notice] Apache/2.0.55 (Ubuntu) mod_fastcgi/2.4.2 PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a mod_perl/2.0.2 Perl/v5.8.7 configured -- resuming normal operations
[Tue Mar 20 11:57:55 2007] [error] server reached MaxClients setting, consider raising the MaxClients setting

---

### Post by Mr. C. on 2007-03-20
Kirk, 

If you are using prefork or thread ?

You have raised MaxClients, but not ServerLimit as required.

What type of content are you serving ?  Static or dynamic ?  KeepAlive doesn't make sense for dynamic content.

Are you using mod_perl ?  If so, have you reviewed: [http://perl.apache.org/docs/1.0/guide/performance.html#KeepAlive](http://perl.apache.org/docs/1.0/guide/performance.html#KeepAlive)

MrC

---

### Post by cap10kirk on 2007-03-21
I reviewed the link that you gave me, and it was pretty educational. The info was very educational, even though its a little beyond me at this point. However, I did tweak my settings based on its recommendations, and I'm running out to buy the max ram I can this weekend.

If you are using prefork or thread ? I don't know.

What type of content are you serving ? Static or dynamic ? I use a CMS to make my pages. I do serve music and videos off my site.

Thanks for your help.

---

