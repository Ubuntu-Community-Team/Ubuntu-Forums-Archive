---
title: "TwikiGues can't login"
date: 2008-09-18
forum: Server Platforms
---

### Post by sublime78ska on 2008-09-18
I installed Twiki on ubuntu server 8.04.  Although I know the TwikiGuest password, when I would go to the configure page at [http://192.168.1.2/cgi-bin/twiki/configure](http://192.168.1.2/cgi-bin/twiki/configure) I would get the login dialog after logging in.  No error msg about invalid user or password.

I changed the apache directive where it checks for configure from deny all to allow all and then I was able to get to the configure page.

However, I still can't login with TwikiGuest.

Does anyone know what I should check for?  I've been searching documentation for a couple days and haven't had any luck.  Most of what I found assumes I installed on a workstation not a server

Thanks in advance!
Phil

---

### Post by elbeano on 2008-09-25
I'm having the same problem. If anyone has a good, step by step, guide to installing this thing, please post it. Everything I've found, including at twiki.org, leaves a lot of steps out. I will keep struggling and post again if I come up with something.

---

### Post by sublime78ska on 2008-09-26
Besides Twiki, I tried Moin Moin, MediaWiki and JSPWiki.  I've decided to go with JSPWiki.  This is just for home use.

---

