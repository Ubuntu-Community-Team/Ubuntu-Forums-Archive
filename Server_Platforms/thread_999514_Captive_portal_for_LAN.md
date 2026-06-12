---
title: "Captive portal for LAN"
date: 2008-12-01
forum: Server Platforms
---

### Post by jason_Xtreme on 2008-12-01
is there a way to force users to visit a local page (intranet) dont need any auth just wanna remove the "i didnt see it" excuse when we post thngs. my other option is to manually change each user's FF setting and that leave IE

---

### Post by cdenley on 2008-12-02
> **jason_Xtreme said:**
> is there a way to force users to visit a local page (intranet) dont need any auth just wanna remove the "i didnt see it" excuse when we post thngs. my other option is to manually change each user's FF setting and that leave IE

I know it's possible because I have a server doing it right now. However, it gets a little complicated for me to post a guide. There is plenty of software which is supposed to function as a captive portal, but I haven't tried it. If you have a spare computer, I suggest you try pfsense.
[http://en.wikipedia.org/wiki/Captive_portal#Software_Captive_Portals](http://en.wikipedia.org/wiki/Captive_portal#Software_Captive_Portals)
[http://doc.pfsense.org/smiller/Captive_Portal.htm](http://doc.pfsense.org/smiller/Captive_Portal.htm)
I've used it as a router before, but never tried the captive portal functionality.

One problem I have experienced with the captive portal solution is if the first page a user connects to uses SSL encryption ([https://)](https://)), you can either drop/reject the connection, allow it even though they haven't seen your page, or display your page with an invalid certificate which results in a warning which confuses most users.

---

### Post by jason_Xtreme on 2010-12-22
just coming back to the ubuntu forums after a Looooong while thanks for the tips, I never did get it to work though, I just put it on staff to know that all the information is there. thanks anyway

---

### Post by windependence on 2010-12-22
[www.pfsense.org]("http://www.pfsense.org")
 
captive portal built right in
 
-Tim

---

