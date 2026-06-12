---
title: "File/Webserver Apache problem"
date: 2008-12-20
forum: Server Platforms
---

### Post by masque7 on 2008-12-20
I've just recently set up a LAMP server, everything is working as it should, however I've got myself into a mess.

I'm hosting dynamic DNS with no-ip.com, therefore I can access my server anywhere. I access it for sFTP and torrentflux, etc. 

What I also want to be able to do is host my own website. The problem I'm having is with Apache. The default root directory for apache to show is /var/www (and the big "It works!), which is fine - because that's where torrentflux is, so I can access that. However, if I change the directory from /var/www to whatever else, I won't be able to access it. I don't think you can move the torrentflux directory because it's dependent on being in /var/www because of apache.

of course, /var/www is a root directory so I can't just move index.html into there.

any ideas how I can host a website and the aforementioned side-by-side?

---

### Post by cariboo on 2008-12-20
You can have as many sub directories as you want in /var/www. Personally I run phpmyadmin, webmin, mediawiki, mp3act webalizer and webbaker. To access a different site, I just use [http://localhost/wiki](http://localhost/wiki) for example to access the wiki. If I was really serious about his, I would setup virtual web sites, but I'm to lazy to do that. [Here]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") is a howto for virtual web sites.

Jim

---

