---
title: "Apache2 serving only through localhost, not even through LAN"
date: 2006-07-24
forum: Server Platforms
---

### Post by harisund on 2006-07-24
I installed apache2 and everything is fine. I am able to access my pages through [http://localhost](http://localhost)

However, if I go to another machine, even on the same LAN, it is not able to connect at all. 

Netstat reveals port 80 is indeed open and being listened on. 

Anyone familiar with any apache directives or something I need to modify? 

(PS: Doesn't work on my Fedora Core box as well. If you have any experience, I would really be grateful)

---

### Post by Johnsie on 2006-07-24
is the machine apache is on running a firewall? If not then it might be problem with the settings on your router or your machine might not be connected to the netwrok properly. Trying piging it :-)

Sorry if that's not much help...

---

