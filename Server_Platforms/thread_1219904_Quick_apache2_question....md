---
title: "Quick apache2 question..."
date: 2009-07-22
forum: Server Platforms
---

### Post by paul.maddox on 2009-07-22
Hi all,

I've noticed that with Apache2 Debian/Ubuntu, it will automatically add .php extensions to the URLs:

So if I have:

[http://localhost/login.php](http://localhost/login.php)

I can go to:

[http://localhost/login](http://localhost/login)

and it will still work - which is nice.


How can I replicate this behavior on another distro? Is it a mod_rewrite trick?

---

### Post by paul.maddox on 2009-07-22
Sorry, answered my own question here!

If anybody is ever interested... You just need to turn on the MultiViews directory option

[http://httpd.apache.org/docs/2.0/content-negotiation.html](http://httpd.apache.org/docs/2.0/content-negotiation.html)

---

### Post by ulidtko on 2009-07-22
> **paul.maddox said:**
> 
You just need to turn on the MultiViews directory option

[http://httpd.apache.org/docs/2.0/content-negotiation.html](http://httpd.apache.org/docs/2.0/content-negotiation.html)

You did the search a bit faster :D

---

