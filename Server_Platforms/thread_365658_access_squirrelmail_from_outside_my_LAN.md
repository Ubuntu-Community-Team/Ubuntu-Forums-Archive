---
title: "access squirrelmail from outside my LAN"
date: 2007-02-19
forum: Server Platforms
---

### Post by reckless2k2 on 2007-02-19
2 questions I'm hoping someone can help me with:

1 - How can I access squirrelmail from outside of my LAN? I'm not sure if it's as simple as opening port 80 and directing it to my box.

2 - How can I change the squirrelmail lookup from [http://mydomian.com/squirrelmail](http://mydomian.com/squirrelmail) to [http://mydomain.com/webmail](http://mydomain.com/webmail) or [http://webmail.mydomain.com?](http://webmail.mydomain.com?)

Thanks for any help.

---

### Post by MJN on 2007-02-20
(Me again!)
 
1. Squirrelmail is just a PHP website being served by Apache so, yes, if port 80 is open and forwarded to your server then you're good to go.
 
2. Changing the squirrelmail path is simply a case of renaming (moving) the squirrelmail directory name. To use it as per your latter suggestion ([http://webmail.domain.com](http://webmail.domain.com)) you'd need to set webmail.domain.com up as a <virtualhost> in Apache with its document root set to that of where Squirrelmail is installed.
 
I'd be more specific however my SM installation is not from scratch and not the repositories hence I don't know how the package modifies Apache as default. If you post your /etc/apache2/apache2.conf and /etc/apache2/sites-available/000-default then I could specify exactly what config you need.
 
Mathew

---

