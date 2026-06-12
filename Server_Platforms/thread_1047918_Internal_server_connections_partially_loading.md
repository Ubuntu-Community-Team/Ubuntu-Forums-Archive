---
title: "Internal server connections partially loading"
date: 2009-01-22
forum: Server Platforms
---

### Post by R.Bucky on 2009-01-22
I have a home network with a LAMP server (8.04 ([http://buckyspalace.net]("http://buckyspalace.net"))), Ubuntu (8.04), and 2 Vista machines. **The problem is that I can only completely connect to my domain address on my network from my server box. Otherwise, I have to use my hostname (e.g. [http://hostname.local](http://hostname.local)) address**. I use Concrete5 CMS for the main pages, Wordpress for my Blog and HowTo's, Jibberbook for the guestbook, and I also have some hand-coded PHP pages. 

Using my other non-server Ubuntu box, I can access the hand-coded php pages no problem. However, the Wordpress pages only show the text after a short 2-5 second delay. The Concrete5 pages do not show up at all. Mind you, I have to use my hostname address (e.g. [http://hostname.local](http://hostname.local)). I cannot get anything using my domain name, except on my server box. 

I recorded the phenomena using a desktop recorder so that you can see what I am talking about ([http://buckyspalace.net/shared/buckyspalace.ogg]("http://buckyspalace.net/shared/buckyspalace.ogg")). It is 2MB and 38 seconds long. The first address is a tabbed hand-coded php page, second is my homepage, third is a WP page (HowTo), fourth is a WP (Blog) pages that partially loads, and the fifth is my Jinzora media server. 

I CAN access phpmyadmin and Webmin perfectly, no problem.

Here is my /etc/hosts file:
```
127.0.0.1 localhost
127.0.1.1 buckyspalace.net markserver markserver.local
```

Help a guy out?

---

