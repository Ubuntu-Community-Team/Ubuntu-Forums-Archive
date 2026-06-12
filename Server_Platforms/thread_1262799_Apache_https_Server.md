---
title: "Apache https Server"
date: 2009-09-10
forum: Server Platforms
---

### Post by Stormspace on 2009-09-10
I have a web site running on my home server that I access from wherever, however I find that I am sometimes blocked by various filtering technologies. ;) I can access the webmin portal on the box using it's port via https however, so it's escaping the block somehow. My thought is to have the website mirrored somehow as an https site so I can still access it. I'd be using a port other than  the one being used by webmin however. 

How do I get Apache to server up encrypted pages(https) for a specific virtual web site?

---

### Post by wirelessmonkey on 2009-09-10
A rather consise set of instructions found here:
[http://beginlinux.com/blog/2009/01/ssl-on-ubuntu-810-apache2/]("http://beginlinux.com/blog/2009/01/ssl-on-ubuntu-810-apache2/")

---

### Post by recentcoin on 2009-09-10
Well, what you're talking about with webmin is a bit tricky.  You have to use IP based virtual hosting in order to have more than one https site on a box (which webmin is using).

---

