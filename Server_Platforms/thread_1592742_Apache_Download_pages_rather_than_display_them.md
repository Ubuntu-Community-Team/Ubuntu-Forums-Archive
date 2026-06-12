---
title: "Apache: Download pages rather than display them"
date: 2010-10-10
forum: Server Platforms
---

### Post by BigCheese01 on 2010-10-10
I have an Ubuntu server with Apache 2.2, but for some reason, it prompts me to download the html and php files rather than displaying them as webpages. 

My .htaccess seems to be correct:
```
AddHandler php5-script .php
AddType text/html .php
```

And the php5 module is enabled and seems to be working. 

It just started happening (it was working fine before). What could be the problem?

---

### Post by jaypeesmith on 2010-10-11
This seems to be happening to me, too.  With 10.04, I never had this issue.  I am wondering what might have changed in 10.10.

---

### Post by HermanAB on 2010-10-11
Well, it means that modphp is unhappy or not loaded.  You should look in the Apache log file for an error message and google it for a solution.

---

### Post by kevin11951 on 2010-10-11
There was an update to Ubuntu 10.04 that removed libapache2-mod-php5.  Reinstall it, and all will be right with the world again...  You may also have to re-enable it as well.

---

### Post by kevin11951 on 2010-10-11
> **kevin11951 said:**
> There was an update to Ubuntu 10.04 that removed libapache2-mod-php5.  Reinstall it, and all will be right with the world again...  You may also have to re-enable it as well.

Oh, and if that doesn't help, try these commands:

```
chown -R www-data:www-data /var/www
chmod -R 0755 /var/www
```

---

### Post by BigCheese01 on 2010-10-14
Hmmm neither of those seemed to help.

I just realized upon a restart that I am getting these warnings with Apache:

[IMG]http://i53.tinypic.com/5x4z9h.png[/IMG]

I can't seem to figure out how to fix them, though, or whether it pertains to my current problem.

---

### Post by BigCheese01 on 2010-10-17
*Bump*

How much trouble do you think it would be to do a full reinstall of apache? 

I've managed to fix the error of mixing ports, but I'm still getting problems trying to get apache to serve the pages.

I really need to get this website finished soon. Can anyone help?

---

