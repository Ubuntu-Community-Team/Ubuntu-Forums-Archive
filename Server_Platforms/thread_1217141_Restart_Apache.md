---
title: "Restart Apache"
date: 2009-07-19
forum: Server Platforms
---

### Post by georgerobbo on 2009-07-19
How do you restart apache in ubuntu server. I had it on the top of my head, but I forgotten. =(

---

### Post by smeerbartje on 2009-07-19
> **georgerobbo said:**
> How do you restart apache in ubuntu server. I had it on the top of my head, but I forgotten. =(

[Click](http://www.google.nl/search?hl=nl&q=how+to+restart+apache+ubuntu&sourceid=navclient-ff&rlz=1B3GGGL_nlNL336NL336&ie=UTF-8), first hit.

---

### Post by ibutho on 2009-07-19
```
/etc/init.d/apache2 restart
```
To reload after making a config change,
```
/etc/init.d/apache2 reload
```

---

### Post by ArchCast on 2009-07-19
> **ibutho said:**
> ```
/etc/ini.d/apache2 restart
```To reload after making a config change,
```
/etc/ini.d/apache2 reload
```

I think you meant init.d ?

---

### Post by ibutho on 2009-07-19
Yeah, its a typo.

---

### Post by brtsos on 2011-01-23
Try this program :

[http://apache-switch.webuda.com/](http://apache-switch.webuda.com/)

It’s very easy to use. You can turn on, turn off or restart apache server.

---

### Post by ksudbury on 2012-02-18
This guide will walk you through the [Ubuntu restart Apache]("http://techspotting.org/ubuntu-restart-apache-stop-start-apache") procedure. 

Hope that helps...

---

