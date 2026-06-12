---
title: "ntop doesn't work"
date: 2006-07-13
forum: Server Platforms
---

### Post by patrickkw on 2006-07-13
I am working in ubuntu 6.06 and I install ntop. It works in port 3000. But did not work for apache proxy. (Refer to [http://www.ntop.org/UsageNotes.html](http://www.ntop.org/UsageNotes.html)) It is missing the tilte bar. Anyone help for anyway it can work for normal http port 80 services? Great Thanks

---

### Post by FredSambo on 2006-07-13
maybe you should give us a little more information.  we need to be warmed up like a crock pot.

---

### Post by patrickkw on 2006-07-14
I use universe apt to install ntop with the followings apache2.conf   


-- Start --
<Proxy *>
        Order deny,allow
        Deny from all
        Allow from all
</Proxy>

ProxyPass /ntop/ [http://localhost:3000/](http://localhost:3000/)
RewriteEngine On
RewriteCond %(HTTP_REFERER) mysite.com/ntop
RewriteCond %(REQUEST_URI) !^/ntop
RewriteRule ^/(.*)$ http://mysite.com/ntop/$1 [L,P]
-- End --

Enclose please find the screen spot. (no title bar to have other option)

---

### Post by saltydog on 2008-02-11
Have you fixed this problem? I am experiencing the same on the https server.

---

