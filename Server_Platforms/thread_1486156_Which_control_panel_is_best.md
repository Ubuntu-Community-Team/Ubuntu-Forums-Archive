---
title: "Which control panel is best?"
date: 2010-05-17
forum: Server Platforms
---

### Post by ct_roy on 2010-05-17
Hi guys,

I've followed some excellent guides on howtoforge for setting up ispconfig on 9.04 which I've managed to get semi-working :) I also installed syscp which doesn't seem to conflict too much with ispconfig.

My question is which open source/free control panel do folks find works best with ubuntu 9.04?

Any past experiences are highly welcome!

Thanks,

ct

---

### Post by dudumomo on 2010-05-17
I'm running Webmin with Ubuntu Server 9.10. So far so good, but I didn't try any other web panel, so I don't really know which one is the best...

---

### Post by ct_roy on 2010-05-17
thanks dudumomo

i'm going to try a fresh local virtual slice of 9.04 and install webmin to compare with ispconfig on my production machine

---

### Post by AzharHafiz.com on 2010-06-22
ehcp no?

---

### Post by TodAB on 2010-07-10
I tried EHCP.  Do not EVER use this in production.  There is no meaningful uninstall procedure and it leaves security controls all over the place.  I had to rebuild my server.  :mad:

---

### Post by sh1ny on 2010-07-10
I am using ispconfig. So far i can't be happier with something that costs $0.

---

### Post by HermanAB on 2010-07-10
Webmin, Usermin and Virtualmin.  This combo is kinda crummy but it gets the job done.

---

### Post by abaden on 2010-07-10
I'd look at ISPConfig. IMHO, Webmin makes things too complicated - it's easier to just learn the config files. Webmin also takes hours to setup - but it's pretty powerful and you have a lot of customization options. ISPConfig is a bit simpler, more recent, and prettier, which end users like.

If you just need a control panel for a few services, like MySQL or Apache, I'd look at some of the service specific control panels. For example, the Cherokee web server includes a pretty slick control panel, and phpmyadmin is great for MySQL related tasks.


Alex

---

### Post by frontline3k on 2010-07-21
Syscp has kinda stop development, so [Froxlor]("http://www.froxlor.org") was borned.

Has support for Debian and Ubuntu, including 10.04.

Take a look, I'm a happy user :p

---

### Post by arrrghhh on 2010-07-21
No one has mentioned eBox?  I believe it's the 'official' replacement for Webmin...

---

### Post by lisati on 2010-08-03
Webmin does the job nicely for me, and I found it to be a breeze to set up.

---

### Post by arrrghhh on 2010-08-03
> **lisati said:**
> Webmin does the job nicely for me, and I found it to be a breeze to set up.

I love Webmin, just heard that the way it installs packages is not good.

I also had an issue with the new service change with init scripts, but I figured out how to tell Webmin to handle it.

---

