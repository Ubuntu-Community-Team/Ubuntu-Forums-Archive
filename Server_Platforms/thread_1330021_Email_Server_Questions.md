---
title: "Email Server Questions?"
date: 2009-11-18
forum: Server Platforms
---

### Post by ductiletoaster on 2009-11-18
Ok so i have a web domain lostpropaganda.net
and im hosting it through my own server Ubuntu 9.04 server edition...
i wanted to be able to have an email server so i could email anyone and receive emails from anyone.
I found this [tutorial]("http://flurdy.com/docs/postfix/") and it sounds promising but i dont want to get into it and not be able actually email yahoo, hotmail, gmail users and so on...
what are my options..?

---

### Post by ductiletoaster on 2009-11-18
Ok a more specific question do i need shorewall if my server is behind a router with an active firewall?

Would it be redundant or a good idea....? 

shorewall is a firewall of sorts!

ANYONE!!!

---

### Post by wyldfury on 2009-11-18
A second firewall shouldn't necessary.

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
[http://www.postfix.org/STANDARD_CONFIGURATION_README.html](http://www.postfix.org/STANDARD_CONFIGURATION_README.html)
[http://www.postfix.org/docs.html](http://www.postfix.org/docs.html)
[http://www.postfix.org/documentation.html](http://www.postfix.org/documentation.html)

The link to the Ubuntu community site should give you the basics. If you want anything beyond that then have a look at the postfix links.
Howtoforge also tends to have some good tutorials, but I don't think there's an Ubuntu specific set of instructions.

---

### Post by HermanAB on 2009-11-18
Note that the absolutely easiest mail system to set up is Citadel.  Go to Citadel.org and try their Easy Install script.

---

