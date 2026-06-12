---
title: "Where can I find mod_negotiation for apache?"
date: 2006-03-07
forum: Server Platforms
---

### Post by jefflee on 2006-03-07
hi everyone, it's my first post in ubuntu form.

I installed apache manual and put it on the web server so I can read it by browser.
but everytime I click a manual page I got:

Not Acceptable
An appropriate representation of the requested resource /manual/index.html could not be found on this server.

Available variants: 
index.html.de , type text/html, language de, charset iso-8859-1 
index.html.en , type text/html, language en, charset iso-8859-1 
.................

  I searched apache.org and seems I should set the default language in the configuration of  mod_negotiation. but I can't find libapache2-mod-negotiation by apt-cache. I searched the web but still get nothing.
  Is there such a package in ubuntu?  
  Thank you.

---

### Post by kmi on 2006-03-07
You  can check if mod_negotiation is compiled with apache2 (it IS apache2, isn't it ?) with :
```
apache2 -l
```
It will show you all the "compiled in modules"...

If it is in the list, edit /etc/apache2/apache2.conf and look for "negotiation". Just a few lines after that, you'll see a line beginning with "LanguagePriority". Is it what you needed ?

Let me know... :)


[Oh ! Welcome jefflee ! :D]

---

### Post by jefflee on 2006-03-09
Thank u!
It's compiled in.
oh I find another compiled-in module I just looked for...

---

