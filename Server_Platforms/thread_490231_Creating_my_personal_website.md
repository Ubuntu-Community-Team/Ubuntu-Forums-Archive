---
title: "Creating my personal website"
date: 2007-07-02
forum: Server Platforms
---

### Post by niicky on 2007-07-02
Hi! I have a recently installed ubuntu server 7.04 (the latest i think thats the version number) on an old box

Its working perfectly internally, and i've installed openssh, and can now access the box both over the internet and internally using the correct IP address. I can view any webpages I host on /var/www/ but only internally nothing from an external source.

I understand that I require a DNS, and have registered with dyndns.com and have created the dynamic DNS [www.niick.is-a-geek.com](www.niick.is-a-geek.com).

when asked for an interface using ddclient I entered ppp0

However I have not a clue what to do next. Please keep in mind that my linux knowledge is basic at best and I may have to set slowly through stages of this happening.

Thank you so much in advance. If i have failed to provide any information please just ask and I will post it here

---

### Post by milton1 on 2007-07-02
Could be a problem with how apache is configured. Try this page:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

or it could be a firewall issue. I recommend Firestarter for managing firewall. Use it to open the necessary port (80 or 443) to outside viewers.

---

