---
title: "Ubuntu Server + Apache + Modules?"
date: 2010-06-15
forum: Server Platforms
---

### Post by dellegazze on 2010-06-15
I have a box running Ubuntu server and Apache 2.2. How do I install/load/whatever Ubuntu modules? I've been searching all over the place and can't find a thing. Maybe my search terms aren't good enough.

Anyway, what I really want to do is install and use mod_include. I've run a server on mac os x before and (I believe) mod_include came out of the box, but I still had to edit the httpd.conf, which I'm totally comfortable with.

Any help (even "google such-and-such words", or "hey, here's a really good tutorial") is greatly appreciated.

---

### Post by cadriel on 2010-06-15
Try running;

```

sudo a2enmod

```

The mod you're after is listed there as "include".

Running this command will essentially enable the mod for you to use.

--
Craig.

---

### Post by dellegazze on 2010-06-15
Hm. That seems to have worked; however, even after adding "Options +Includes" and "XBitHack on", chmod +x-ing index.html, and restarting apache, I still get nothing for "<!--#include virtual="/includes/header" -->". There is indeed a file at /includes/header, and this exact directory works on OS X.

Help?

---

### Post by dellegazze on 2010-06-15
Ah, I got it. For anyone with the same problem, I edited /etc/apache2/sites-available/default to have "+Includes" under <directory /var/www/>, restarted apache, and everything worked.

Thanks for the help!

---

