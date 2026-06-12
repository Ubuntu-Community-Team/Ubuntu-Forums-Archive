---
title: "How to open Apache only for local LAN?"
date: 2009-09-14
forum: Server Platforms
---

### Post by UranUtan on 2009-09-14
Hi,

I am learning PHP, MySQL on Ubuntu Desktop 9.04 x64. I got everything working as instructed by various tutorials.

However, I would like the Apach server on my computer to respond only to machines within the local LAN, subnet 192.168.1.x.

Thanks in advance for any help.

---

### Post by Iowan on 2009-09-14
If you don't have the router forwarding a port, the server *should* be isolated from internet, but there may be a way to limit access in a config file (I'll need to look it up).

---

### Post by paulisdead on 2009-09-14
[http://www.communitymx.com/content/article.cfm?cid=A56D5](http://www.communitymx.com/content/article.cfm?cid=A56D5)
This is probably more what you're looking for, since you can keep the administrative directories locked down, but allow general folders to be accessed anywhere.

---

### Post by UranUtan on 2009-09-15
Hi,

It's true, I have no port forwarding set in my router. But for the sake of learning, I am still interested by a more explicit rule. Following Paul's link. that the .htacess file that does the trick. Combining with the advices of another blog [http://www.thelinuxblog.com/htaccess-allow-from/](http://www.thelinuxblog.com/htaccess-allow-from/)

So all I need is to create a file named .htaccess in the root folder of the web server and put these lines
```
Order Deny,Allow
Deny from all
Allow from 192.168.1.1/24
```
Thanks very much for your helps.

---

