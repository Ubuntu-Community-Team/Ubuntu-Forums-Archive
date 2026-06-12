---
title: "ufw disable &amp;&amp; ufw enable???"
date: 2010-02-21
forum: Security
---

### Post by TheDarkSix on 2010-02-21
I wad reading [http://mauroandres.wordpress.com/2009/12/14/build-a-secure-desktop-firewall-with-ufw-part-i/](http://mauroandres.wordpress.com/2009/12/14/build-a-secure-desktop-firewall-with-ufw-part-i/)

It said after i typed some settings to enter "ufw disable && ufw enable" But the firewall just disabled and did not Enable afterwards.

maybe i read it wrong? maybe i was suppose to type sudo ufw disable and THEN sudo ufw enable 2 different times...lol

and uh i typed ufw show arg and it said i needed to be root? and i notice it isn't even a valid command? but why did it say i needed to be root?

i have a lot of studying ahead of me

---

### Post by Pjotr123 on 2010-02-21
Maybe this will help to clarify:
[http://sites.google.com/site/easylinuxtipsproject/security#TOC-Firewall](http://sites.google.com/site/easylinuxtipsproject/security#TOC-Firewall)

---

### Post by bodhi.zazen on 2010-02-21
You need to use sudo with those commands.

---

### Post by chascon on 2010-02-23
The intro states, "Administration of ufw is entirely done as root in this article. Use sudo if preferred.". The article was written/researched with root (su). So if Ubuntu's default sudo doesn't allow &&'d commands (doubt it), or if you you have to use sudo because that's what Ubuntu has by default (and it does) use sudo.

If you want to use su, you'll have to configure your system to do so.

---

### Post by bodhi.zazen on 2010-02-23
> **chascon said:**
> The intro states, "Administration of ufw is entirely done as root in this article. Use sudo if preferred.". The article was written/researched with root (su). So if Ubuntu's default sudo doesn't allow &&'d commands (doubt it), or if you you have to use sudo because that's what Ubuntu has by default (and it does) use sudo.

If you want to use su, you'll have to configure your system to do so.

If you wish a root shell, use 

```
sudo -i
```

---

### Post by memilanuk on 2010-02-23
> **bodhi.zazen said:**
> If you wish a root shell, use 

```
sudo -i
```

Interesting... I'd always just ran 

```
sudo su -
```

which appears to do about the same thing (give a login shell as root), but your version is shorter and neater ;)

---

