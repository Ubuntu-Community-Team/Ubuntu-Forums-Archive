---
title: "Configuring Apache"
date: 2010-04-18
forum: Server Platforms
---

### Post by imbty on 2010-04-18
Hey, guys. This place has been a lot of help, but once again, I'm stuck on something. Here's the background.

I have a domain. 
imbty.com -> hosted by GoDaddy and it points to their servers
imbty.imbty.com -> temporarily points to my home server

The directory for imbty.imbty.com was /var/www by default, but I've pointed it to /testing/my/server .

Anyways, when I go to [http://imbty.imbty.com/](http://imbty.imbty.com/) it doesn't load properly. It's suppose to look like [http://www.imbty.com/](http://www.imbty.com/)

It seems fairly simple, but Webmin is really hard to understand. I don't even know what BIND DNS was. I thought I needed that to be able to direct my subdomain to my homes server.

---

### Post by volkswagner on 2010-04-18
It is likely a file permission issue with a config file or formatting file such as .css.

---

### Post by tenlientl on 2010-04-18
Yea. I'm actually having a hard time even trying to setup an FTP user for /var/www .

I use Webmin. I can setup an FTP, but I can't have different users directed to different paths. Can't as in I don't know how.

edit: okay. I just made *.css into 755. Still no luck.

---

### Post by tenlientl on 2010-04-18
Got it. Thanks, guys.

---

