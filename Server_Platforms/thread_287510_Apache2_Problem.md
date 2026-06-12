---
title: "Apache2 Problem"
date: 2006-10-28
forum: Server Platforms
---

### Post by Kodai on 2006-10-28
Hello! I've had apache2 webserver for some time now, it's worked great. I have php/perl/mysql and what ever else comes w/ the default package.  It's always worked fine, until this evening, when there was a brief power outage, a few seconds, and the server was on at the time. Now; when ever I try to go to my website (kodai.mine.nu) it tries to download every page unless it's an html page, then it'll work. But any CGI or PHP pages will not work. I try and restart Apache, and I get this error.

```
 * Forcing reload of web server  (Apache2)...
(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
   ...fail!


```

Please Help!!!

---

### Post by Kodai on 2006-10-28
so i fixed the problem.. kind of...

I still have a problem

If i connect to my website, using an internal or external ip. everything works fine, if i connect using my static DNS name, it works fine, but if i connect using my dynamic DNS name, kodai.mine.nu it wants to download the front page.... All the other pages work fine. the .php, .html, .cgi, everything works fine, except the first page.

[http://kodai.ath.cx/](http://kodai.ath.cx/) works fine though....

whats going on >.>

(even when i turn my server off, and i do kodai.mine.nu, it asks me to download my main page, and it's always junk)

---

