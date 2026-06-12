---
title: "Web-based SSH?"
date: 2007-11-25
forum: Server Platforms
---

### Post by prodezigner on 2007-11-25
Anyone know where I can find a web-based SSH program? I have PuTTy on my Flash drive but I don't carry it around everywhere I go, and when I visit family a few counties over it'd be nice to just open a browser and admin my home server. Or even when I'm at school would be nice also...

---

### Post by GigaVolt on 2007-11-25
[http://mgeisler.net/php-shell/](http://mgeisler.net/php-shell/)

---

### Post by MJN on 2007-11-25
Proceed with extreme caution.... PHP Shell looks like an accident waiting to happen. Remember SSH has been developed with security at the forefront, whereas PHP Shell could never achieve this given it is reliant on PHP.

I'm not aware of a suitable alternative (there may well be some so don't take that as a reason to not hunt around) but what I do is host a copy of the Putty executable on my server and if I need to SSH remotely simply download/run it on the host machine (it doesn't need to install - it can run in a single-file standalone mode). Of course this is no use on locked down systems that don't allow the execution of arbitrary applications but that's never been an issue for me.

Mathew

---

### Post by supirman on 2007-11-25
There are java applets available to do what you're looking for.  

[http://www.appgate.com/products/80_MindTerm/](http://www.appgate.com/products/80_MindTerm/)  
That one is free for personal use.

Or, you could surely google for java ssh applet and you should be able to find others.

This way, you can put it on your own web server and utilize ssh from anywhere.

---

### Post by HermanAB on 2007-11-25
Web based SSH == HTTPS

---

### Post by MJN on 2007-11-25
> **HermanAB said:**
> Web based SSH == HTTPS

Not at all.

SSH = Secure Shell
HTTPS = HTTP over SSL/TLS

They serve entirely different purposes.

Mathew

---

