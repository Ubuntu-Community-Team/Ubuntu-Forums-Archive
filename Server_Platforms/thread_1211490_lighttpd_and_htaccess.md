---
title: "lighttpd and htaccess"
date: 2009-07-12
forum: Server Platforms
---

### Post by kennedy7 on 2009-07-12
Hello I have been using apache2 webserver and Ubuntu for a long time. But now I do allot of media converting with a youtube copy called "ostube" which puts allot of load on my 850mhz proc.
With apache2 I can setup htaccess to restrict anyone who doesnt enter the right password but now since I have switched to a lighter webserver "lighttpd" I cant use htaccess. What is the access file for lighttpd or how can i make lighttpd use htaccess files?
Any help? Thanks guys

---

### Post by abaden on 2009-07-12
I'm not very familiar with Lighttpd, but I do know that one of the drawbacks is it does not support .htaccess files (as the developers see them as adding too much bloat - one more config file to read slows down the server). I didn't see any documentation for denying access to directories doing a quick search either.

However, have you considered nginx? It's a new, lightweight, superslick web browser that is powering some major sites out there (wordpress and hulu, for example). They also have excellent documentation, and are in the apt repository. 

Here's the main [nginx]("http://nginx.org/") site, and here's the [wiki article]("http://wiki.nginx.org/NginxHttpCoreModule") with a bit on how to deny somebody from a location.

HTH

---

### Post by kennedy7 on 2009-07-12
is there a way i can make you have to enter a password to enter a directory in lighttpd webserver? Id really like it cause i have a private website with lots of files on it and i dont want people to take them.

---

### Post by cybernet on 2009-08-09
[http://www.imminentweb.com/technologies/lighttpd-secure-configuration](http://www.imminentweb.com/technologies/lighttpd-secure-configuration)

Have FuN:P

---

